# Open Source Graphics 101: Getting Started - Boris Brezillon, Collabora

Talk is:

* Explaining how GPUs work
* Explaining Linux OSS Graphics Stack

## Graphics pipeline

Vertices, Textures, Transformation -> GPU -> 3D object

## Stages

* Geometry stage
* Rasterizer stage

## Geometry stage

* Model vertices
* Vertex shader
  ** Model view projection transform
  ** Other
* Geometry / Tessalation Shaders
* Primitive assembly, clipping, culling, viewpoint transform

## Rasterizer stage

* Triangle set-up
* Fragment shader <- Textures
* Merging stage (Alpha blending, Late depth testing)

## GPU Internals

* Generic shader core
  ** ALUs
  ** Load/store unit
* Caches
* Schedulers
* Texture units
* Triangle set-up units
* Rasterisers
* Blending units
* ...

## Let's go massively parallel

* Parallelization, how hard can it be?
  ** Stalls caused by memory access -> Caches, Multi-threading
  ** SIMD: try to get all ALUs busy: Avoid conditionals, pack similar operations

## Interaction with your GPU

* CPU remains in charge
* How?
  ** Put everything in memory
  ** Trigger GPU
  ** Evented on completion
* GPU Command Stream

## Linux graphics stack

* Graphics API's:
  ** OpenGL, GLX, EGL, Direct3D, Vulkan, WSI
* Userspace drivers
* ...

## Graphics API: What is it?

* Entry point for graphics apps / libs
* Abstract the GPU pipeline config / manipulation

## The Graphics API: Shaders

* Part of the pipeline is programmable:
  ** Separate programming language

## Graphics API: OpenGL(ES) vs Vulkan

* 2 philosophies
  ** OpenGL hides max complexity
  ** Vulcan provides fine-grained control
  ** Vulcan offers record / replay of operations
  ** More work for developer, less for CPU
* Vulcan apps more verbose, but:
  ** Can be leveraged by high level API's
  ** You will learn how things work

## Kernel / userspace separation

* Drivers as well as drivers are complex
  ** Minimal complexity in kernelspace
  ** Easier to debug userspace

## Kernel drivers

* Deal with: Memory, command stream submission / scheduling, interrupts / signalling
* Open-source drivers live in-tree, proprietary drivers live out-of-tree

## Userspace driver

** Expose one for several Graphics APIs
** Interacts with windowing manager

## Mesa: Open source userspace driver

* 2 graphics APIs
  ** OpenGL(ES), Vulkan

## Mesa state tracking: Pre-gallium

* Tried to abstrace all the state-machine specificities
* No longer used

## Mesa State Tracking: Vulkan

* Thinner layer between app and driver

## What's next?

* GPU topic is vast!
* Start small
* Get a grasp on concepts / implementation takes time
* Don't give up


