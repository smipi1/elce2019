# Timing Boot Time Reduction Techniques - Michael Opdenacker, Bootlin

BBB + Webcam

Initial boot time (boot to first frame) 9.45 s

## Optimization principles

1. Optimize what doesn't limit further progress
1. Start with slow storage + less efficient compression to amplify phenomena to observe
1. Start from last parts of boot time and finish by the kernel. End with the boot.

## ARM vs Thumb2

Size reduction with Thumb2

## uClibc vs musl

## Optimize apps

* Reduce features to essential only
* Total reduction 350 ms

## Init reductions

* `bootchartd` eliminate unnecessary services

## Rootfs size reduction

* Smaller filesystem may be faster to mount
* `initramfs` more efficient: single load

## Init and rootfs optimizations

* Replace init scripts with 1
* Simplify busybox config
* Eliminate unused files

## Static executables

* Works well with few executables

## Filesystem optimizations

* Switching to `initramfs`
* Remove block and MMC support to compensate for decompression
* Disable initramfs compression (else compressed twice)
* Total boot time slightly lower than at start

## Kernel optimizations

* Use `initcall_debyug`
* Capture boot-log
* Script to graph
* Postpone module loading if possible
* Remove tracers
* ...

## Preset loops per jiffy

## Multiprocessor support

* SMP is quite slow to initialize
* Enabled by default

## Kernel module support

* Unselect features progressively + make copies of config

## Silence the console

* `quiet`
* `CONFIG_PRINTK`
* `CONFIG_CALLSYMS`

## CONFIG_EMBEDDED / CONFIG_EXPERT

* Remove system calls

## Thumb2 kernel code

* Didn't work
* Requires disabling ARM unwind

## Memory allocators

Stick to SLAB

## Kernel compression

* LZO / gzip best solutions (hardware dependent)

## Optimize kernel for size

* Os a bit faster than O2

## Remove `proc` filesystem

* Remove `sysfs`

## Other optimizations

* Disable `CONFIG_DEBUG_INFO`
* Disable `CONFIG_UNWINDER_ARM``

## Append DTB to kernel

## Bootloader optimizations

* U-Boot falcon mode: No Environment
* U-Boot falcon mode + DTB

## Results

2.4 s (> 1 s to probe USB)


