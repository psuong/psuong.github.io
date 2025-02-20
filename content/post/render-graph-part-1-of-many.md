---
title: "Render Graph Part 1 of Many"
date: 2022-12-24T18:23:53-05:00
draft: true
---

For sometime, Unity has been working on a RenderGraph API, which is an abstraction on top of SRP
Render Passes. A pass/node in a RenderGraph states what kinds of resources the Render Graph uses 
at that stage and manages those resources for you.

Now HDRP has started to integrate and utilize the RenderGraph system and URP is likely underway as 
Unity attempts to sort of "unify" the different render pipelines.

I thought it would be a good time and idea to dive into it and create a forward/deferred renderer 
using strictly the RenderGraph. I don't want these series of blog posts to be a tutorial series so 
I'm going to focus on the core render graph passes/nodes.

Now, when doing any kind of rendering the first thing we want to do is get anything on screen. Usually 
a triangle in NDC space if you're doing the "Hello World!" version of graphics programming, but 
in our case, we just want `MeshRenderer`s that we place in the scene to appear on the screen.

## The RenderGraph

The RenderGraph is pretty straight forward. We initialize a `RenderGraph` in a `RenderPipelineAsset`. 

```cs
RenderGraph graph;
...

public LuxRenderPipeline(LuxRenderPipelineAsset pipelineAsset) {
    graph = new RenderGraph("Lux_Render_Graph");
    ...
}
```

The next major part is overloading the `Render` function. I'm focusing on the more 
modern implementation which takes a `List<Camera>` as a parameter instead of an array.

```cs
public override void Render(ScriptableRenderContext context, List<Camera> cameras);
```

The first thing we do in SRP is we begin and end the context for rendering. This calls 
any delegates that we need to run before and after rendering.

```cs
GraphicsSettings.useScriptableRenderPipelineBatching = luxRP.UseSrpBatcher;
BeginContextRendering(context, cameras);
...

// Towards the end of the function call
EndContextRendering(context, cameras);
```

We loop through each camera and begin and end the Camera rendering and perform a bulk of 
the work with rendering.

```cs
foreach (var camera in cameras) {
    BeginCameraRendering(context, camera);

    if (!camera.TryGetCullingParameters(out var cullParams)) {
        EndCameraRendering(context, camera);
        continue;
    }
    var cullResults = context.Cull(ref cullParams);

    // Set up projection matrices
    context.SetupCameraProperties(camera);

    var cmdBuffer = CommandBufferPool.Get("Execute_Render_Graph");
    var renderGraphParams = new RenderGraphParameters {
        executionName = "Lux_Render_Graph_Execute",
        commandBuffer = cmdBuffer,
        scriptableRenderContext = context,
        currentFrameIndex = Time.frameCount,
        rendererListCulling = true
    };

    using (graph.RecordAndExecute(in renderGraphParams)) {
        GraphPasses.ExecuteBasePass(camera, graph, cullResults, luxRP.ShadowSettings);
    }

    context.ExecuteCommandBuffer(cmdBuffer);
    CommandBufferPool.Release(cmdBuffer);

    context.Submit();
    EndCameraRendering(context, camera);
}
```

We grab the `ScriptableCullingParameters` first and if we can't then we early out and end
our camera rendering context. If we have a valid `ScriptableCullingParameter` then we can 
reconfigure our struct and cull with those parameters.

```cs
if (!camera.TryGetCullingParameters(out var cullParams)) {
    EndCameraRendering(context, camera);
    continue;
}
var cullResults = context.Cull(ref cullParams);
```

## Setting up a CommandBuffer
Command Buffers store a series of commands that will be played back at a later stage, 
effectively a queue.

All command buffers are requested via the `CommandBufferPool` and our render graph will
queue up commands during each pass.