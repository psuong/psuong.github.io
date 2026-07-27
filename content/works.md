---
title: "My Works"
layout: single
---

Over the last decade, I've worked on a various number of projects professionally.

# InitialPrefabs, LLC
- Co-founded with my brother in June 2016, where we did consulting work for the following companies.
- Developed [NimGui](https://initialprefabs.gitlab.io/imgui.book/), a 1 draw call user interface to
allow developers to draw using an immediate mode API. NimGui processes 20k vertices in 0.38 ms/frame 
on a Ryzen 5 5600.
- Integrated [font packing with MSDF](https://github.com/InitialPrefabs/InitialPrefabs.Msdf) in Rust
interoping with C# to reduce font atlas disk size by 30% and improve atlas generation times by 2x 
via lockless multithreading to a single image. 
- Developing a [TaskGraph](https://initialprefabs.com/tools/c-taskgraph/) in C99 with an API similar 
to Unity’s Job System, work stealing, cyclic dependency prevention, and automated bindings to other 
languages via Cpp.AST.NET.

## PHYND
- Developed C# & C++ SDK to support Unity Game Engine (v2017LTS -> 6.0LTS) and Unreal Engine 
(v4.6 -> v6.1) enabling low latency in-game video/audio cloud streaming on a Ryzen 5 5600 
(2.5ms time frame).

## The Feast
- Developed a custom deferred non physically based render (NPBR) pipeline in URP allowing
better scalability when authoring many spot lights.
- Developed custom Amplify shader templates to 
- Developed a procedural spot light system using indirect rendering to visualize enemy detection range.
- Developed a runtime CPU culling system using spatial maps for interior levels allowing unnecessary 
objects to be culled reducing frametime from 8ms to 5ms on a NVIDIA GTX 1080.

## Cell To Singularity
- Developed a backward compatible save game schema to replace the existing save game schema allowing 
players to have multiple saves and to rollback their existing save to an earlier version.

## ESC Game Theater (Defunct)
- Developed a customize rendering system to allow ESC Game Theater to render thousands and millions 
of sprites via WebGL on stadium jumbotrons

## Metamorphosis Games
- Developed an hierarchical finite state machine (HFSM) to allow the game designers to author more 
complex behaviours using a node like system.
- Glued behaviour states to override the animation's state machine allowing animations to blend 
consistently.

## VrWiz (Defunct)
* Developed a pipeline to trim Unity's terrain system and bake it as a custom mesh to draw 
with indirect rendering
* Developed a procedural tree system allowing the player to design their own tree and use that tree
to draw indirectly through out the entire world.
* Developed custom Blinn-Phong shaders using LUTs and reduced render texture allocations on runtime 
to optimize the frame time to run at 72 FPS on the Oculus Quest.

## KungFu Kickball
* Trained machine learned agents to play KungFu Kickball in order to fill a lobby with feasible and 
believable bots instead of using behaviour trees to design the behaviors.

## Mokuni Games
- Developed procedural level generation reducing the amount of time spent designing reasonable levels 
for Kitty in the Box 2.
- Developed a force and penetration detection system for Kitty in the Box VR on the HTC Vive. This 
prevents the virtual hands from clipping directly into the the main character's body.
- Developed an efficient navigation sampling system to allow NPCs to quickly navigate between 
platforms.

## Metis Suns
- Developed a visualization system to display the state of BoB's individual thought nodes.
- Developed a dampening system to normalize force to ensure that BoB's individual nodes do not 
violently react under extreme pressure.
    - Developed a pipeline to store control attendee inputs to help normalize the forces from attendees.
- Developed a neural network based utility theory system allowing NPCs to constantly evaluate needs 
with multi agent coordination/support for Emissary in the Squat of Gods.
- Developed an node based graph editor allowing designers to develop agent sensors and behaviours 
with minimal inputs from the developers for Emissary in the Squat of Gods.

# Thousand Ant
- At Thousand Ant, I was a technical writer and software engineer helping other companies build 
technical demos and writing easy to digest technical documentations.

## Kart Microgame {#kart}
My team and I were responsible for updating Unity's Kart Microgame to match more modern arcades. Some 
features I contributed to the project include:

* New game modes
* Mobile WebGL optimizations for low end phones
  * Optimized a 35ms runtime on Samsung S6, iPhone6s, & Google Pixel 1  to 18 ms
  * Please visit the link [here](https://psuong.gitlab.io/kart-silver/) to test the game on mobile
* ML Agents integration (check out the video below)

[Asset Store Link](https://assetstore.unity.com/packages/templates/karting-microgame-150956)

## [HyperCastle](https://thousandant.itch.io/hypercastle-explorer)
- Developed an SVG parser to parse all unique unicodes and pack them efficiently on runtime.
- Developed a custom glyph renderer to draw all glyphs within the SVG with culling support in 
orthographic and perspective mode for efficient rendering.

![hypercastle-3d-visualization](https://img.itch.zone/aW1hZ2UvMTU3NzM1Mi85MjE5NDY4LmpwZw==/original/t4Drrk.jpg)

## Tutorials for Unity
Below are a bunch of video tutorials I have written the scripts and recording to. Narration was done 
by a professional voice actor.

### Flocking with the C# Job System {#flocking}
[![Flocking with the C# Job System](https://img.youtube.com/vi/KJZoSV-JX5I/0.jpg)](https://www.youtube.com/watch?v=KJZoSV-JX5I "Flocking")

### C# Job System: Using DOTS with Managed C# APIs {#jobs}
[![C# Job System](https://img.youtube.com/vi/tlG0DAXF09U/0.jpg)](https://www.youtube.com/watch?v=tlG0DAXF09U "Managed API")

### Bolt {#bolt}
[![bolt](https://img.youtube.com/vi/aQceChK-kC4/0.jpg)](https://www.youtube.com/watch?v=aQceChK-kC4 "Bolt")

### Adaptive Performance {#adaptive-perf}
[![adaptive-performance](https://img.youtube.com/vi/d5O4Uw6gPBI/0.jpg)](https://www.youtube.com/watch?v=d5O4Uw6gPBI "Adaptive Performance")

### Physics Optimizations {#physics}
[![physics-optimization](https://img.youtube.com/vi/pTz3LMQpvfA/0.jpg)](https://www.youtube.com/watch?v=pTz3LMQpvfA "Physics Optimizations")

### Shader Graph Feature Video {#shadergraph}
[![shader graph](https://img.youtube.com/vi/-QcwEYOHt2I/0.jpg)](https://www.youtube.com/watch?v=-QcwEYOHt2I "Shader Graph 10")

### Editor Scripting with UI Toolkit {#uitoolkit}
[![ui toolkit](https://img.youtube.com/vi/mTjYA3gC1hA/0.jpg)](https://www.youtube.com/watch?v=mTjYA3gC1hA "UI Toolkit")

### Scriptable Objects Tutorial {#scriptableobjects}
[![scriptable objects](https://img.youtube.com/vi/PVOVIxNxxeQ/0.jpg)](https://www.youtube.com/watch?v=PVOVIxNxxeQ "Scriptable Objects" )

### Kart Microgame Updates & Video {#mlagents}
[![ml agents](https://img.youtube.com/vi/gYwWolRFt98/0.jpg)](https://www.youtube.com/watch?v=gYwWolRFt98 "ML Agents")

### Device Simulator {#devsim}
[![device simulator](http://img.youtube.com/vi/uokF9CmUs9c/0.jpg)](https://www.youtube.com/watch?v=uokF9CmUs9c "Device Simulator")

## Tutorials for Genvid Technologies {#genvid}
Genvid provides a streaming engine solution to help interface Twitch viewers with the game they are 
viewing by allowing interactions between the viewers and streamers through customize interfaces!

[![genvid-sdk-1](http://img.youtube.com/vi/yfI6txN0l3A/0.jpg)](http://www.youtube.com/watch?v=yfI6txN0l3A "Genvid SDK Pt. 1")
[![genvid-sdk-2](http://img.youtube.com/vi/q9_3O7dCPOg/0.jpg)](http://www.youtube.com/watch?v=q9_3O7dCPOg "Genvid SDK Pt. 2")
[![genvid-sdk-3](http://img.youtube.com/vi/liUBiHi1N8M/0.jpg)](http://www.youtube.com/watch?v=liUBiHi1N8M "Genvid SDK Pt. 3")
[![genvid-sdk-4](http://img.youtube.com/vi/1pFk7Havww0/0.jpg)](http://www.youtube.com/watch?v=1pFk7Havww0 "Genvid SDK Pt. 4")