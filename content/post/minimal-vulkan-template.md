---
title: "Minimal Vulkan Template"
date: 2025-02-19T08:40:02-05:00
draft: false
summary: "Writing my own template for app creation and having fun doing so"
---

Not too long ago, I read Sebastian's blog post, [Programming Without Friction](https://blog.s-schoener.com/2025-02-03-programming-friction/) 
and I was also in the need to try and practice Vulkan. In the same fashion, I started building out my own finance tool 
using [egui](https://www.egui.rs/), [winit](https://github.com/rust-windowing/winit), and [vulkan-ash](https://github.com/ash-rs/ash). 

I have had some experience trying to build out a vulkan app in [C++](https://github.com/psuong/VulkanRendering) first 
and through my attempts of my own game [engine](https://github.com/psuong/geometroid), but that effort is 
inconsistent due to the usual reasons of life. _So_, I needed something with smaller effort and started to 
work on my own opiniated CSV editor for my own finance. While Google Sheets, LibreOffice Calc, Excel 
all exist and _works_, it won't fit my need of building something small and getting more comfortable rewriting 
Vulkan code.

After a few nights of exploring egui's APIs and looking how to get the mesh data, I ended up getting something 
working quite nicely.

![csv-editor](/images/min-vulkan-template/csv-editor.jpg)

Some features, I ended up going with are (left to right based on the screenshot).

## Side Panel
* loading/saving csv files
* adding/removing rows
* filtering by month and/or category (pretty happy with this one, I'm just using bit flags to figure out how to filter)
* editing the categories

## Central Panel
* main table with clickable rows, drag and drop, editing values in the csv

## Right panel
* quick summary to view stats (WIP)

Eventually, I want to explore plotting so I can visualize data from my CSV. Like I said, all of this 
I can do already in any off the shelf CSV editor, but this is more fun for me. I even ended up with a 
[template](https://github.com/psuong/min-vulkan-template) I can continuously fork to create small apps 
that run at 60 fps. It doesn't support things like images yet, mainly because I don't have a _need_ to 
load and display images, but if I do, I can always update the template.
