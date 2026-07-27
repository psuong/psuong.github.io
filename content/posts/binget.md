---
title: "binget"
date: 2025-03-05T10:52:54-05:00
draft: false
summary: "Building a cli to grab releases from Github."
tags:
    - cli
    - c#
---

A little while ago I wrote a small [client](https://github.com/psuong/binget), `binget`, formerly 
called LspManager, to automate pulling the latest binaries from Github Releases from repos I mainly 
use. This was mainly to pull debuggers and LSPs executables because of my setup with Neovim.

I wrote this in C# because I wanted to 

- a. Do more C# in a .NET environment
    - I've mainly been doing `mono` with Unity for the longest time, which is a slightly different environment.
    - If I were to create DLLs, they would strictly target **C# 9** and **.NET 2.1 Standard**.
    (I was being really patient with CoreCLR integration in Unity but it looks like it's taking longer, 
    understandably.)
    - On a side note, I am doing a lot of .NET 8 (and .NET Standard 2.1) dlls for [games](https://github.com/InitialPrefabs)! 
    (I'll be dabbling with Vulkan/OpenGL for C#. Of course, depending on how much time I have.)
- b. Play around with NativeAOT compilation pipeline.
    - I would only create Native DLLs with C++ and Rust and interop them C#. Although fun, sometimes 
    I don't want to create the bindings manually and I haven't had the time to look into an automated 
    process yet (or build one).
- c. Although not exclusive to C#, I also wanted to play with **Github actions**. Being in games, I often 
    work with custom pipelines that are not usually on Github.

## So what does **binget** do?
`binget` reads from a `config.toml` that you supply. There you would define 
* the base url to download from,
* the repositories to get the contents
* the target you actually want

An example would be the following:
```
url = "https://api.github.com/repos/"
destination = "your-destination-path"

[[repositories]]
name = "OmniSharp/omnisharp-roslyn"
target = "omnisharp-win-x64.zip"
display = "omnisharp"

[[repositories]]
name = "LuaLS/lua-language-server"
target = "win32-x64.zip"
display = "lua"

[[repositories]]
name = "shader-slang/slang"
target = "windows-x86_64.zip"
display = "slang"
```

You would execute `binget.exe /path/to/your/config.toml` and would get a screen similar to the following 
in your terminal:

```
➜ .\binget.exe .\config.toml
[Url]: https://api.github.com/repos/OmniSharp/omnisharp-roslyn/releases/latest, [Target]: omnisharp-win-x64.zip, [Zip]: \language-servers\omnisharp-win-x64.zip
██████████████████████████████████████████████████ 100.0% - https://github.com/OmniSharp/omnisharp-roslyn/releases/download/v1.39.13/omnisharp-win-x64.zip.zip
Cleaned up zip and extracted to: \language-servers\omnisharp

[Url]: https://api.github.com/repos/LuaLS/lua-language-server/releases/latest, [Target]: win32-x64.zip, [Zip]: \language-servers\lua-language-server-3.13.6-win32-x64.zip
██████████████████████████████████████████████████ 100.0% - https://github.com/LuaLS/lua-language-server/releases/download/3.13.6/lua-language-server-3.13.6-win32-x64.zip
Cleaned up zip and extracted to: \language-servers\lua

[Url]: https://api.github.com/repos/shader-slang/slang/releases/latest, [Target]: windows-x86_64.zip, [Zip]: \language-servers\slang-2025.6.1-windows-x86_64.zip
██████████████████████████████████████████████████ 100.0% - https://github.com/shader-slang/slang/releases/download/v2025.6.1/slang-2025.6.1-windows-x86_64.zip
Cleaned up zip and extracted to: \language-servers\slang
```

Now this utility is supposed to kept pretty minimal, so versioning is _not_ supported, I just pull 
the latest. Since the utility pipes everything to console, I kept the console logic pretty minimal 
too. I.e, if I am outputting too much for a single console to contain, I just leave don't output 
the content that's offscreen.
