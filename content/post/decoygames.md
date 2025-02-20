---
title: "Decoy Games, LLC"
date: 2024-08-27
draft: false
pinned: true
categories:
  - work
tags:
  - work

summary: "The work I have done @ Decoy Games, LLC"
---

At Decoy Games, I was a Senior Engineer & Graphics Programmer where I

## Rendering
* Developed rendering features
    * Developed a non photorealistic shader to render characters in DOTS with 
        * procedural rim lighting
        * emission blending
        * gradient ramping to achieve visual target
    * Developed custom post processing effects (bloom, screen space outlines, etc) to target specific rendering layers without affecting everything universally
    * Developed and implemented concepted VFX created by the art team with a custom architecture to maintain particle count efficiency and throughput

## Maintenance
* Planned low level archithecture for efficient memory usage 
* Added initial set of unit tests to ensure build stability
* Standardized usage of C# source generators/analyzers to provide static analysis
* Analyzed project wide performance of runtime/resource usage to identify regressions to address in future sprints

## Custom Tooling
* Developed workflows for the Art team(s) using **UI Toolkit/Yoga** & **Unity ImGui**
    * Optimized animation pipeline by splitting workload of animation processing onto multiple threads bringing processing time from 4 hrs to 3 minutes for 300,000 animation curves
    * Created a bulk importer for the character team to
        * Quickly import a large number of characters
        * Assign the correct shader + texture combinations to each part of the character
    * Automate import settings through a custom Scriptable Import Pipeline
    * Developed a custom animation timeline allowing the Art team to bind gameplay logic events to animations separately from animation clips
        * Allows multiple artists to edit timelines and add events safely avoiding complicated merge conflicts

## Team Growth
* Mentored more junior devs in thinking about Data Oriented Design & being performance aware of the code they write
* Explained technical limitations for visual features desired by the team
