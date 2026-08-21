---
title: "Writing a BindGenerator"
date: 2026-08-20T22:49:56-04:00
draft: false
summary: "Creating a binding generator in C#"
tags:
    - c#
    - c
    - interop
---

So, I am working on [TaskGraph](https://initialprefabs.com/tools/c-taskgraph/), an asynchronous batch scheduler that lets 
you, the developer, queue up tasks with dependencies.

This means that you can create a daisy chain of tasks and schedule them to be executed on multiple threads. Tasks can 
be independent or they an rely on other tasks before execution. Independent tasks will be executed first because they 
do not rely on anything to run before them.

Now, the project is written in C99 with the intention that I have bindings for other languages, with the first target 
language being C#. 

# A Bind Generator Workflow
A bind generator typically needs to parse the "public" header files so that it can generate PInvoke callbacks to call 
unmanaged code.

For example let's say we have a public function in our header.

```c
int add(int a, int b);
```

This is a simple `add` function that takes two integers to calculate the sum. Now the C# equivalent that is PInvoke is, 

```cs
[DllImport("some-library.dll", CallingConvention = CallingConvention.Cdecl, EntryPoint = "add", ExactSpelling = true)]
public static extern int Add(int a, int b);
```

Breaking it down, what the C# side is doing is declaring that the function `Add` is an `extern` function which means that 
it is declared and implemented externally. The parameters for the `DllImport` attribute in order are:

- `"some-library.dll"` - The name of the dll to import.
- `CallingConvention = CallingConvention.Cdecl` - The calling convention, i.e how should the function be invoked? 
In this case we say cdecl, which is the standard calling convetion for C & C++ programs in windows. 
The stack is cleaned up by the caller.
- `EntryPoint = "add"` - The entry point, which is the name of the function.
- `ExactSpelling = true` - And whether or not the function to find should be bounded by exact spelling.

Writing this by hand is pretty simple, but can be tedious when the core API changes when we add or remove structs and functions.

# Writing the BindGen Tool
So the language of choice I used to create my automatic bind generator is C#. I'm using 
[ConsoleAppFramework](https://github.com/Cysharp/ConsoleAppFramework), [Scriban](https://github.com/scriban/scriban), and
[CppAst](github.com/xoofx/CppAst.NET) as my main frameworks.

## ConsoleAppFramework
ConsoleAppFramework has been my go to framework for small command line programs.

## Scriban
Scriban is a templating engine I use to template out C# files written with C# 9. I am picking an old version of C# because 
I want to support Unity. The idea is that I write templates out for structs, enums, unions, and hotload functions and I pass
info that is parsed from my `C` header files to the templates.

## CppAst.NET
CppAst.NET is my primary choice of parsing as it can resolve `typedef`s to their original type. Lets say I have the following,

```c
typedef LONG atomic_long_t;
```

CppAst.NET will resolve `atomic_long_t` to `LONG`, which itself, is a `typedef` to the builtin type, `long`. Because 
this provides the builtin type, I have a unified baseline to convert `C` types to `C#` types based on the target platform ABI.

For example, with Windows, a `long` is 32 bit, but on Unix platforms, they are 64 bit. CppAst.NET provides these 
diagnostics.

# Creating a Dependency Tree
In C order of declaration matters. Take the example code below,

```c
typedef struct { 
    int value;
} A;

typedef struct {
    A a;
} B;
```

The struct, `A`, needs to be defined first before being used in the struct, `B`. Like my TaskGraph, I build my own 
dependency tree my own dependency tree, but for types and fields first. This means I will generate `struct A` first 
before parsing and generating `struct B` in C#.

Why does this matter?

Ultimately, I want the C# API to be idiomatic and _look_ like C#. I have functions and structs written in snake_case and 
I transform those structs to be written in PascalCase. The structs generated will have the exact same size in C# and C to 
prevent unknown behaviors during runtime, but the names will be different.

Once the types have been transformed and cached, I iterate through all fields with my structs, pull renamed types, 
and feed them to my Scriban templates.

This is an example of how my Scriban template looks like. 

```cs
namespace InitialPrefabs.TaskGraph {
    /// <summary>
    /// {{ summary }}
    /// </summary>
    public{{ if is_unsafe }}unsafe{{ end }} struct {{ name }} {
{{- for field in fields }}
        internal {{ field.type }} {{ field.name }};
{{- end }}
    }
}
```

For a struct, I will pull all of the fields and their names, any comment found in my `C` header file. If the struct 
contains a pointer that is not transformed to either a `UIntPtr` or `IntPtr` in C#, it will be marked `unsafe`.

Functions are similar, where I parse every C function, pull their parameters and types, and then generate the PInvoke 
version of the API.

Ultimately, this tool will help me maintain TaskGraph since I just have to run a command line program to regenerate 
my C# API. Eventually, I will support other languages since I can add multiple options to my bind generator to target
more than just C#.
