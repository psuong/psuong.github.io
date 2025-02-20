---
title: "NimGui Brief"
date: 2024-09-10
draft: false
pinned: false
categories:
  - ui
tags:
  - ui

summary: "NimGui, a 1 draw call ImGui for Unity"
---

![NimGui Banner](https://assetstorev1-prd-cdn.unity3d.com/package-screenshot/61ad3e69-6145-42a0-ad27-47d178ad2b90.webp)

**[Asset Link](https://assetstore.unity.com/packages/tools/gui/nimgui-a-1-draw-call-ui-209126)**

## Background
I needed a way to quickly draw functional UI for debugging purposes that 
* was a static API (no inheritance)
* seamless with MonoBehaviours or any Entity Component System (DOTS or any Third Party system)
* high performance

With those needs, I ended up building NimGui over time as my internal go to library. Many of the inspirations came from
DearImGui and eGui. While interopting those libraries was an option, I wanted something that was primarily C# and easy to 
install. 

Most details of the implementation and architecture can be found at the [documentation website](https://nimgui.initialprefabs.com/).