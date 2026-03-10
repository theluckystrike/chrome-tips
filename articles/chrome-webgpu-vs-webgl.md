---
layout: post
title: "Chrome WebGPU vs WebGL Comparison"
<<<<<<< HEAD
description: "Compare WebGPU vs WebGL in Chrome: performance benchmarks, API differences, use cases, and migration guide for web developers."
date: 2026-01-15
categories: [web-development, graphics, performance]
tags: [webgpu, webgl, chrome, graphics, web-development, performance]
=======
description: "Compare WebGPU vs WebGL in Chrome: performance benchmarks, API differences, use cases, and migration guide. Learn which graphics API is right for your web projects."
date: 2026-01-15
categories: [technology, chrome, graphics, web-development]
tags: [webgpu, webgl, chrome, graphics-api, web-development, performance]
>>>>>>> consumer/a66-chrome-webgpu-vs-webgl
author: theluckystrike
---

# Chrome WebGPU vs WebGL Comparison

<<<<<<< HEAD
The world of web graphics is evolving rapidly, and Chrome has been at the forefront of bringing powerful graphics capabilities to the browser. For years, WebGL has been the standard for hardware-accelerated graphics on the web, enabling everything from interactive games to data visualizations. Now, WebGPU is emerging as the next-generation API that promises better performance, more modern design, and greater flexibility. If you are a web developer or someone interested in browser graphics technology, understanding the differences between these two APIs is essential for making informed decisions about your projects.

Chrome has already enabled WebGPU by default in recent versions, making it accessible to developers who want to explore its capabilities. This comprehensive comparison will walk you through everything you need to know about WebGPU versus WebGL, including performance characteristics, API differences, practical use cases, and a practical migration guide. By the end of this article, you will have a clear understanding of when to use each technology and how to approach transitioning your existing projects.

## Understanding the Basics

Before diving into the comparison, it is helpful to understand what each API brings to the table. WebGL, which stands for Web Graphics Library, is a JavaScript API that allows browsers to render interactive 2D and 3D graphics using the GPU. It is based on OpenGL ES, a widely-used standard for embedded systems. WebGL has been available in Chrome since 2010 and has become the foundation for countless web applications, games, and creative tools.

WebGPU, on the other hand, is a newer API designed from the ground up to address the limitations of WebGL. It is based on modern graphics APIs like Vulkan, Metal, and DirectX 12, which offer better performance and more control over GPU resources. WebGPU was developed by the W3C GPU for the Web Community Group and represents a significant leap forward in browser graphics capabilities.

One of the key philosophical differences between the two APIs is their approach to GPU resource management. WebGL uses a relatively high-level approach that abstracts away many底层 details, which makes it easier to learn but also limits performance optimization opportunities. WebGPU exposes more of the GPU's capabilities directly to developers, giving them finer control over how resources are allocated and used.
=======
The world of web graphics is evolving rapidly, and if you are developing browser-based applications that rely on rendering, you have likely heard about WebGPU and WebGL. These two APIs represent different generations of graphics programming for the web, and understanding their differences is essential for making informed decisions about your next project. Whether you are building a game, a data visualization tool, or a creative application, choosing the right graphics API can significantly impact performance, developer experience, and the eventual reach of your application.

Chrome has been at the forefront of implementing both WebGL and WebGPU, giving web developers powerful tools to create immersive experiences directly in the browser. However, the two APIs are not simply two options for achieving the same result. They have fundamentally different architectures, capabilities, and trade-offs that make each one suitable for different scenarios. This comprehensive comparison will help you understand those differences and guide you toward the right choice for your specific needs.

## Understanding WebGL: The Established Standard

WebGL, which stands for Web Graphics Library, has been the go-to solution for hardware-accelerated graphics in browsers since its initial release in 2011. Based on OpenGL ES, WebGL provides a JavaScript API for rendering interactive 2D and 3D graphics within any compatible web browser. For nearly a decade, it was the only game in town for high-performance web graphics, and it powers countless applications ranging from simple data visualizations to complex browser-based games.

The architecture of WebGL is built around the concept of the fixed-function pipeline, although modern versions expose programmable shaders that give developers more control over the rendering process. Developers write GLSL (OpenGL Shading Language) code for vertex and fragment shaders, which are compiled and executed on the GPU. This approach, while powerful, requires developers to manage many low-level details manually, from memory allocation to state management.

One of WebGL's greatest strengths is its widespread support. Virtually every modern browser, including Chrome, Firefox, Safari, and Edge, supports WebGL 1.0, and WebGL 2.0 is supported in all major browsers as well. This universal compatibility means that any application built with WebGL can run on almost any device with a capable GPU, making it an excellent choice for projects that need maximum reach.
>>>>>>> consumer/a66-chrome-webgpu-vs-webgl

However, WebGL also has notable limitations. The API was designed to mirror OpenGL ES 2.0, which itself was based on older graphics programming concepts from the early 2000s. While extensions and WebGL 2.0 brought some modern features, the underlying architecture remains constrained by its legacy. Performance can suffer when applications need to issue many draw calls, and the CPU overhead of managing WebGL state changes can become a bottleneck for complex scenes.

<<<<<<< HEAD
When comparing WebGPU versus WebGL, performance is often the first topic that comes up, and for good reason. WebGPU is designed to extract more performance from modern GPUs by reducing overhead and enabling more efficient rendering pipelines.

In benchmark tests, WebGPU consistently demonstrates superior performance compared to WebGL, particularly in scenarios involving complex scenes, large numbers of objects, or compute-intensive operations. The performance gains can be substantial, with some tests showing improvements of 30% to 50% or more depending on the workload. These improvements come from several factors working together.

First, WebGPU reduces CPU overhead by minimizing the number of API calls needed to perform rendering operations. It achieves this through a batched submission model that allows multiple commands to be prepared and sent to the GPU in a single call. This is particularly beneficial for applications that need to render many small objects, such as particle systems or games with dense environments.

Second, WebGPU supports compute shaders, which allow general-purpose GPU computing beyond traditional rendering. This opens up possibilities for physics simulations, data processing, machine learning inference, and other compute-intensive tasks that were difficult or impossible to implement efficiently in WebGL.

Third, WebGPU's memory management model is more explicit, allowing developers to allocate and manage GPU memory directly. This reduces the overhead of automatic memory management and gives developers the ability to optimize memory usage for their specific use cases.

However, it is important to note that performance is not the only consideration. WebGL still performs well for many common use cases, and its maturity means that optimization techniques are well-documented. For simpler applications that do not require the most demanding graphics, WebGL may still be the right choice, especially given its broader browser support and larger ecosystem of existing code and tutorials.
=======
## Understanding WebGPU: The Modern Evolution

WebGPU represents the next generation of graphics and compute APIs for the web, designed from the ground up to address the limitations of WebGL. Developed by the W3C GPU for the Web Community Group, WebGPU provides a modern, GPU-accelerated API that draws inspiration from Vulkan, Metal, and DirectX 12, the most recent graphics APIs used in native application development.

The most significant architectural difference between WebGPU and WebGL is the shift from the fixed-function pipeline model to a more flexible, explicit resource management model. In WebGPU, developers have direct control over GPU resources such as buffers, textures, and pipelines. This explicit approach reduces driver overhead and allows for more efficient batched rendering, which can dramatically improve performance in applications with many objects or complex scenes.

WebGPU also introduces a unified compute API that extends beyond traditional graphics rendering. Compute shaders allow developers to perform general-purpose GPU computations (GPGPU) for tasks such as physics simulations, machine learning inference, particle systems, and data processing. While WebGL could achieve some of these tasks through clever use of fragment shaders, WebGPU provides a dedicated, well-designed compute workflow that is more capable and easier to use.

Another major improvement in WebGPU is its error handling and debugging support. The API is designed to catch errors at validation time rather than causing mysterious rendering artifacts or crashes. This feature alone can save developers countless hours of debugging frustration, especially when working on complex projects with many moving parts.

Chrome enabled WebGPU support starting with version 113, and the feature has matured significantly since then. However, WebGPU does not yet have the same universal browser support as WebGL. While Chrome, Edge, and Firefox all support WebGPU, Safari's support is more limited, and older browsers do not support it at all. This gap is gradually closing, but it remains an important consideration for projects that need to support a wide range of devices.
>>>>>>> consumer/a66-chrome-webgpu-vs-webgl

## Performance Comparison: Raw Numbers and Real-World Impact

<<<<<<< HEAD
The API differences between WebGPU and WebGL reflect their different design philosophies and the evolution of graphics programming over the past two decades. Understanding these differences is crucial for developers considering either API.

WebGL uses an immediate-mode rendering style that can be familiar to developers coming from traditional graphics programming. You create a context, set up shaders, bind buffers, and issue draw calls in a relatively linear fashion. While this approach is straightforward, it can lead to inefficient code if not managed carefully, as the API does not provide strong incentives for organizing rendering logic efficiently.

WebGPU takes a more modern, pipeline-oriented approach. Instead of configuring individual state changes for each draw call, you define entire rendering pipelines that include all the state, shaders, and configuration needed for a particular type of rendering. You then record commands into a command buffer that can be replayed efficiently. This approach encourages better organization of rendering code and enables the GPU to optimize pipeline execution more effectively.

The shader languages also differ significantly between the two APIs. WebGL uses GLSL (OpenGL Shading Language), which has been the standard for graphics shaders for many years. WebGPU uses WGSL (WebGPU Shading Language), a new language designed specifically for WebGPU. WGSL is intentionally designed to be more explicit and less error-prone than GLSL, with stronger type checking and clearer semantics.

Error handling is another area where the APIs differ substantially. WebGL often uses a silent failure model where invalid operations may simply not produce the expected result without raising clear errors. WebGPU uses a validation layer that can be enabled during development to catch errors early, making debugging much easier. This represents a significant improvement for developer productivity.

Resource binding in WebGPU is also more structured. Instead of binding individual resources to specific texture units or uniform locations, you define bind groups that group related resources together. This makes it easier to manage complex scenes with many different types of resources and enables more efficient resource switching on the GPU.
=======
When comparing performance between WebGPU and WebGL, the results can vary significantly depending on the specific workload and hardware configuration. However, several general trends emerge from benchmark tests and real-world usage that are worth understanding.

In scenarios involving many draw calls, such as rendering scenes with thousands of distinct objects, WebGPU consistently outperforms WebGL by a substantial margin. The overhead of each draw call is much lower in WebGPU due to its explicit resource model and reduced CPU-side validation. Games with complex scenes, architectural visualizations, and CAD applications can see performance improvements of two to five times or more when switching from WebGL to WebGPU, particularly on hardware that supports the latest GPU features.

Compute workloads show an even more dramatic difference. WebGPU's dedicated compute pipeline is significantly more efficient than emulating computation through rendering shaders in WebGL. Applications that perform physics calculations, fluid simulations, or machine learning inference on the GPU can benefit from order-of-magnitude performance improvements with WebGPU. This makes WebGPU particularly attractive for applications in scientific computing, AI-assisted tools, and advanced game mechanics.

Memory management is another area where WebGPU often excels. The API allows for more efficient memory reuse and provides better control over GPU memory allocation. Applications that previously struggled with memory pressure in WebGL, particularly on mobile devices with limited VRAM, can often achieve better performance and stability with WebGPU.

However, it is important to note that WebGL still has performance advantages in certain specific scenarios. For simple 2D rendering or applications that issue relatively few draw calls, the difference between the two APIs may be minimal. Additionally, because WebGL has been optimized for decades by browser vendors, some specific rendering techniques may still run slightly faster in WebGL on certain hardware configurations. In practice, the performance gap is narrowing as WebGPU implementations mature, but WebGL remains a viable choice for less demanding applications.

## API Differences: Developer Experience and Workflow
>>>>>>> consumer/a66-chrome-webgpu-vs-webgl

The differences between WebGPU and WebGL extend beyond performance to encompass the entire developer experience. These differences affect how you structure your code, debug your applications, and think about graphics programming.

<<<<<<< HEAD
Understanding when to use each API requires understanding the strengths of each and the requirements of your specific project. Let us explore the typical use cases where each API shines.

WebGL remains an excellent choice for many applications. If you need to support older browsers or devices that may not have WebGPU support, WebGL is still the most widely supported graphics API on the web. Many mobile browsers, older computers, and budget devices have WebGL support but may not have full WebGPU support. If your audience includes these users, WebGL ensures broader compatibility.

WebGL is also well-suited for simpler graphics applications that do not push the boundaries of GPU performance. If you are building a basic 2D game, a simple data visualization, or a lightweight interactive demo, WebGL provides all the capabilities you need with a gentler learning curve. The abundance of tutorials, libraries, and example code makes it easier to get started quickly.

WebGPU is the clear choice for demanding applications that require maximum performance. This includes high-end games with complex 3D scenes, real-time physics simulations, large-scale data visualizations, virtual and augmented reality experiences, and applications that combine rendering with compute operations. If your application would benefit from compute shaders or if you need to render thousands of objects efficiently, WebGPU provides the capabilities you need.

Another compelling use case for WebGPU is machine learning on the web. While WebGL can be used for simple neural network inference, WebGPU's compute shaders and efficient memory model make it much more practical for running larger models in the browser. This is particularly relevant for applications like image recognition, natural language processing, and real-time video analysis.

For developers building tools like Tab Suspender Pro and other Chrome extensions, performance considerations are always important. Even productivity extensions that perform background processing can benefit from WebGPU's compute capabilities when handling large datasets or performing complex calculations.

## Browser Support and Compatibility

Browser support is an important consideration when choosing between WebGPU and WebGL. As of early 2026, WebGPU has made significant progress in terms of browser compatibility, but it is not yet as universally supported as WebGL.

Chrome has had WebGPU enabled by default since version 113, and the feature has been available in Chrome Canary and other Chromium-based browsers for even longer. Firefox has been implementing WebGPU support and has enabled it by default in recent versions. Safari has also added WebGPU support, though the implementation continues to evolve.

Despite this progress, WebGPU support is not universal. Some browsers and devices still lack WebGPU support, particularly older devices and some mobile browsers. If broad compatibility is critical for your project, you may need to implement fallback logic that uses WebGL when WebGPU is unavailable.

Feature detection for WebGPU is straightforward. You can check if the GPU object is available in the navigator and attempt to request an adapter. Many developers are choosing to implement progressive enhancement strategies where they use WebGPU when available and fall back to WebGL when it is not.

## Migration Guide

If you have an existing WebGL application and are considering migrating to WebGPU, the process requires careful planning and understanding of the differences between the two APIs. Here is a practical guide to help you approach this migration.

The first step is to assess whether migration is necessary for your project. If your current WebGL application performs adequately and meets your requirements, migration may not be worth the investment. However, if you are building new features that would benefit from WebGPU's capabilities, or if performance is a critical concern, migration makes sense.

Start by learning WGSL, the shader language used by WebGPU. While GLSL and WGSL share some concepts, there are significant differences in syntax and semantics. Understanding WGSL thoroughly will make the rest of the migration much easier.

Next, familiarize yourself with the WebGPU API structure. The concepts of devices, contexts, pipelines, command buffers, and bind groups will become familiar with practice. The WebGPU specification and the MDN documentation provide comprehensive references.

When porting your rendering code, you will need to rewrite your shaders in WGSL and restructure your rendering logic around the pipeline model. This is typically the most time-consuming part of the migration. Focus on getting your basic rendering working first before attempting to optimize.

One helpful strategy is to implement a hybrid approach during the transition. You can detect WebGPU support at runtime and use WebGPU when available, falling back to WebGL otherwise. This allows you to gradually migrate your codebase while maintaining compatibility with users whose browsers do not support WebGPU.

Expect to encounter challenges along the way. The explicit nature of WebGPU can require rethinking how you manage resources and organize rendering code. Debugging may require different techniques than you are used to with WebGL. However, the improved performance and developer experience are worth the investment for demanding applications.

## Future Outlook

The future looks bright for WebGPU as the graphics API for the web. Browser vendors are actively developing and improving their WebGPU implementations, and the ecosystem of tools, libraries, and tutorials is growing rapidly. Major frameworks are adding WebGPU support, making it easier for developers to take advantage of the new API without writing low-level code.

WebGL will continue to be supported for the foreseeable future, but it is increasingly becoming the choice for legacy applications and cases where compatibility is the primary concern. New projects, especially those with performance requirements, should strongly consider WebGPU from the start.

As WebGPU support continues to improve and expand, we can expect to see increasingly sophisticated web applications that push the boundaries of what is possible in a browser. From immersive gaming experiences to advanced scientific visualizations, WebGPU is enabling a new generation of web graphics applications.

For developers willing to invest in learning WebGPU, the rewards are substantial. Better performance, more modern API design, and access to capabilities that were previously impossible on the web make WebGPU an exciting technology to work with. Whether you are building the next generation of web games, developing creative tools, or creating data visualizations, WebGPU provides the foundation you need to build exceptional experiences.
=======
In WebGL, the primary unit of work is the draw call, and developers manage state through a global context that can be modified at any time. This approach is familiar to developers who have worked with OpenGL, but it can lead to subtle bugs where state changes affect unexpected parts of the rendering pipeline. Debugging WebGL applications often involves inspecting the generated WebGL calls and hoping that the browser's debug tools provide enough information to identify the problem.

WebGPU introduces a more structured approach to graphics programming. Resources are organized into render pipelines, bind groups, and command buffers that explicitly define what will happen on the GPU. This verbosity requires more upfront code to set up, but it provides much better guarantees about what will happen at runtime. Errors are caught early, and the API's design encourages practices that lead to more maintainable code.

The shader languages are also notably different. WebGL uses GLSL, which has been the standard for OpenGL-based graphics for decades. WebGPU uses WGSL (WebGPU Shading Language), a new language specifically designed for the API. WGSL is influenced by GLSL but has different syntax and semantics that reflect WebGPU's architecture. Learning WGSL is an additional investment for developers moving to WebGPU, but it is generally considered easier to write correctly due to its stricter rules and better type system.

One area where WebGL maintains an advantage is the ecosystem of libraries and tools. Three.js, Babylon.js, PlayCanvas, and other major 3D frameworks have built extensive tooling around WebGL. While many of these frameworks are adding WebGPU support, the wealth of tutorials, examples, and community knowledge around WebGL remains unmatched. WebGPU is gaining momentum, but it will take time for the ecosystem to fully mature.

## Use Cases: When to Choose Each API

Understanding when to use WebGL versus WebGPU is crucial for making the right architectural decisions for your project. Each API excels in different scenarios, and the choice should align with your specific requirements.

WebGL remains the best choice for projects that need maximum compatibility. If your application must work on older browsers, low-end devices, or platforms where WebGPU is not yet available, WebGL is the safe default. The API works on virtually everything with a GPU, making it ideal for applications that cannot afford to exclude any users. Marketing websites, educational platforms, and simple interactive visualizations can often achieve everything they need with WebGL without requiring the additional complexity of WebGPU.

WebGPU is the clear winner for performance-critical applications that target modern browsers. If you are building a graphics-intensive game, a real-time data visualization system, a simulation application, or any project where frame rate and rendering complexity are critical, WebGPU provides the capabilities you need. The compute shader support alone makes WebGPU essential for applications that need to perform general-purpose GPU computations alongside graphics rendering.

For applications that fall somewhere in between, consider your team's experience and the long-term trajectory of your project. If you are starting a new project that will be maintained for several years, investing in WebGPU now may pay dividends as browser support continues to improve and as more developers become familiar with the API. On the other hand, if you have an existing WebGL codebase and no compelling reason to migrate, continuing with WebGL is a reasonable choice.

Interestingly, some developers are finding creative ways to use both APIs in the same application. For example, an application might use WebGL for certain rendering passes that work better with the older API while using WebGPU for computationally intensive operations that benefit from the newer API's capabilities. While this hybrid approach adds complexity, it can be useful during a transition period or for applications with diverse requirements.

## Migration Guide: Moving from WebGL to WebGPU

If you have an existing WebGL application and are considering migrating to WebGPU, the process requires careful planning and understanding of the differences between the two APIs. This section provides a practical guide to help you navigate the migration.

The first step is to assess whether migration is necessary for your application. If your application runs well in WebGL and meets its performance requirements, there may be no urgent need to migrate. However, if you are hitting performance ceilings, need compute shader capabilities, or want to take advantage of modern GPU features, migration is worth considering.

Understanding the conceptual differences is essential before writing any code. WebGPU's explicit resource model is fundamentally different from WebGL's implicit state management. Take time to learn about pipelines, bind groups, render passes, and command buffers. The WebGPU specification and the WGSL language specification are the authoritative resources, and the official samples provide excellent examples of idiomatic WebGPU code.

Porting shaders is often one of the more time-consuming parts of migration. WGSL has different syntax and semantics from GLSL, so you will need to rewrite your shader code. Several automated tools exist to help convert GLSL to WGSL, but they are not perfect, and manual adjustment is usually necessary. Pay particular attention to differences in how coordinate systems, data types, and function signatures work between the two languages.

The resource binding model requires significant refactoring. In WebGL, you set uniform values directly through the context. In WebGPU, you organize resources into bind groups that are bound to specific stages of your rendering pipeline. This requires more upfront setup but provides better organization and performance. Plan to spend time designing a bind group strategy that works for your application.

Testing is critical throughout the migration process. Because WebGPU validates more aggressively than WebGL, you may encounter errors that were silently ignored in your WebGL code. These errors are actually helpful because they identify problems that could cause incorrect rendering. Work through each error systematically, and do not be tempted to disable validation for the sake of convenience.

Finally, consider adding feature detection and fallback support. Even after migration, some users may be on browsers that do not support WebGPU. Implementing graceful fallback to WebGL ensures that all users can still access your application, albeit potentially with reduced features or performance.
>>>>>>> consumer/a66-chrome-webgpu-vs-webgl

## Performance Optimization Tips for Both APIs

<<<<<<< HEAD
*Built by theluckystrike — More tips at zovo.one*
=======
Regardless of which API you choose, understanding how to optimize performance is essential for creating smooth, responsive applications. While the specific techniques differ between WebGL and WebGPU, some general principles apply to both.

Minimizing draw calls is one of the most important optimizations for both APIs. Each draw call has CPU overhead, and scenes with thousands of individual draw calls will struggle to maintain high frame rates. Techniques such as instanced rendering, batching, and combining static geometry into single meshes can dramatically reduce draw call counts.

Texture and buffer management also significantly impacts performance. Ensure that your textures are properly sized for their use case, use compressed texture formats when available, and avoid unnecessary data transfers between CPU and GPU memory. In WebGPU, take advantage of the explicit memory management to reuse buffers rather than creating new ones for each frame.

For WebGL specifically, be mindful of state changes. Each change to the WebGL state requires validation and can cause pipeline stalls. Group rendering operations by state to minimize changes. Use extensions like ANGLE_instanced_arrays for efficient instancing when available, and consider using WebGL 2.0 for its improved capabilities.

For WebGPU, invest time in designing efficient pipeline and bind group layouts. Once created, these objects can be reused across frames, so the upfront cost pays off quickly. Use multiple render passes appropriately to organize your rendering into logical phases, and take advantage of the compute shader for operations that do not require rasterization.

## The Role of Browser Extensions: Tab Suspender Pro

While we are on the topic of Chrome and web performance, it is worth mentioning how browser extensions can complement your graphics application's performance. Extensions like Tab Suspender Pro can help manage system resources when users have multiple tabs open, which is particularly relevant for users who run graphics-intensive web applications alongside other browser activities.

Tab Suspender Pro automatically suspends inactive tabs to free up memory and CPU resources. For users who keep many tabs open while working with your WebGPU or WebGL application, this can help ensure that your application has adequate resources available. When users return to suspended tabs, the extension automatically reloads them, providing a seamless experience while helping to maintain overall system performance.

This is particularly useful for web-based games and creative tools that users may leave running in the background while browsing other content. By reducing the resource burden of inactive tabs, Tab Suspender Pro helps ensure that your graphics application can maintain smooth performance even on systems with limited resources.

## Conclusion

The choice between WebGL and WebGPU is not simply a matter of picking the newer option. Each API has its place in the web development landscape, and understanding their respective strengths and limitations is essential for making informed decisions. WebGL provides broad compatibility and a mature ecosystem, making it a solid choice for applications that prioritize reach over cutting-edge performance. WebGPU offers superior performance, modern capabilities, and a better developer experience, making it the preferred choice for demanding applications that target modern browsers.

As web technologies continue to evolve, WebGPU will likely become the dominant graphics API for the web, much like how native applications transitioned from OpenGL to Vulkan and Metal. However, this transition will take years, and both APIs will coexist for the foreseeable future. By understanding both options and their appropriate use cases, you can build graphics applications that perform well today while positioning yourself for the future of web-based graphics programming.

Whether you choose WebGL for its compatibility or WebGPU for its capabilities, the most important thing is to match your technology choice to your specific requirements, your target audience, and your team's expertise. The web platform continues to offer incredible opportunities for creating immersive, interactive experiences, and both WebGL and WebGPU are powerful tools in your toolkit for making those experiences a reality.

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)
>>>>>>> consumer/a66-chrome-webgpu-vs-webgl
