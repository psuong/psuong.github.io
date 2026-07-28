---
title: "Projects"
layout: "single"
url: "/projects"
summary: "projects"
---

# Personal Projects
A bunch of open source projects I've developed/contributed to.

## [BinGet](https://github.com/psuong/binget)
BinGet is a tiny little package manager I wrote for myself in C#. It is a 8.78MB binary that reads a configuration toml 
file to pull archives/binaries from Github. It can list packages, install/update packages, and perform version & 
checksum checking.

## [DocGen](https://github.com/psuong/docgen)
DocGen is a documentation generator that reads and parses docstrings from source code to generate documentation in 
**markdown**.The project is written in .NET 10 and currently supports parsing languages such as **C** and **C#**. 
An example of the documentation generated can be viewed 
[here](https://initialprefabs.com/tools/collections/noallochashset/).

## [Minimal Vulkan GUI Template](https://github.com/psuong/min-vulkan-template)
I wanted to create some really quick apps with an imgui rendering for my UI. This project mainly serves 
as a template for quick rust apps.

## [C# Stackalloc Collections](https://github.com/InitialPrefabs/InitialPrefabs.Collections)
I wanted to write a library that let's me create per frame data structures without needing to allocate on the heap. 
Right now it supports the following data structures: bit array, list, queue, priority queue, hashset, and hashmap.

## [ImportOverrides](https://github.com/InitialPrefabs/ImportOverrides)
![demo](https://github.com/InitialPrefabs/ImportOverrides/blob/main/import-overrides.png?raw=true)

Import Overrides is a custom gui that aims to enhance the import pipeline. When importing Textures 
through a custom asset post processor, you often have to set the texture settings yourself manually 
through code. If you're aiming to create a visual importer, you would need to write the GUI yourself. 
This package provides the GUI by default to `TextureImporterSettings` and 
`TextureImporterPlatformSettings` allowing you to create your own visual scriptable import pipeline.

## [InitialPrefabs.Msdf](https://github.com/InitialPrefabs/InitialPrefabs.Msdf)
![visual](https://github.com/InitialPrefabs/InitialPrefabs.Msdf/raw/main/msdf-comparison-to-sdftmp-2.png?raw=true)

This is an implementation of MSDF Font Rendering. This allows for crispy sharp fonts at a fraction of 
the size compared to SDF rendering. SDF rendering does provide effects such as a glowing effect which 
MSDF loses out on, but that can be remedied by providing an SDF field to the Alpha channel.

This repo shows how to render a glyph orthographically, but does not provide text layout. 
Italics and bold also do not exist at the moment. This work exists to integrate with my custom 1 draw 
call ui: [Nimgui](https://assetstore.unity.com/packages/tools/gui/nimgui-a-1-draw-call-ui-209126).
