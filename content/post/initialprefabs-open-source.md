---
title: "InitialPrefabs Open Source"
date: 2024-10-13T19:57:14-04:00
draft: false

categories:
  - opensource
  - tools
tags:
  - tools

summary: "Some of the works I've done that are open sourced"
---


# [ImportOverrides](https://github.com/InitialPrefabs/ImportOverrides)

![demo](https://github.com/InitialPrefabs/ImportOverrides/blob/main/import-overrides.png?raw=true)

Import Overrides is a custom gui that aims to enhance the import pipeline. When importing Textures through a custom 
asset post processor, you often have to set the texture settings yourself manually through code. If you're aiming to 
create a visual importer, you would need to write teh GUI yourself. This package provides the GUI by default to 
`TextureImporterSettings` and `TextureImporterPlatformSettings` allowing you to create your own visual + scriptable 
import pipeline.

---

# [InitialPrefabs.Msdf](https://github.com/InitialPrefabs/InitialPrefabs.Msdf)
![visual](https://media.githubusercontent.com/media/InitialPrefabs/InitialPrefabs.Msdf/refs/heads/main/Assets/com.initialprefabs.msdfgen/Example/FontAtlas/UbuntuMonoNerdFontMono-Regular_MSDFAtlas.png?raw=true)

This is an implementation of MSDF Font Rendering. This allows for crispy sharp fonts at a fraction of the size 
compared to SDF rendering. SDF rendering does provide effets such as a glowing effect which MSDF loses out on, but 
that can be rememedied by providing an SDF field to the Alpha channel.

This repo shows how to render a glyph orthographically, but does not provide text layout. Italics and bold also do 
not exist at the moment. This work exists to integrate with my custom 1 draw call ui: [Nimgui](https://assetstore.unity.com/packages/tools/gui/nimgui-a-1-draw-call-ui-209126).