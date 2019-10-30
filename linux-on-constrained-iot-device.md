# Running Linux on Constrained IOT Device - Rui Silva, Linaro & Tushar Khandelwal, Arm Ltd.

Rich IoT platforms

## Motivation

* More demanding IoT applications: Mix of Cortex-A / -M
* Security
* Linux: Robust nw stack

## HW System overview

ARM Corstone-700: All firewalled:

* A-Class subsystem
* M-Class subsystem
* Security enclave M-Class
* ROM
* RAM
* Ssytem Control

## Definition

Specs:

* < 4/8MB SRAM
* < 8 MB Flash (NOR)
* Mixed Cortex-A/-M
* Secure enclave Cortex-M0+
* SoC solutions
* Customizable

## SW system overview

* OpenAMP
* MHU's ?
* Cortex-A32
* ...

## Tinification

* Yocto / OpenEmbedded
* On top of Poky-tiny
* musl
* Add S/W component recipes
* Image file using wic tool
* XIP
* Thumb2
* Upstream kernel
* Simgle armv7A arch
* Reduced defconfig
* Read-only FS: cramfs
* XIP support added
* Direct access to flash as mapped (mtd) avoid page cache
* ...
* Read-write filesystem: littlefs
* Try power-loss resiliency, wear leveling, bounded ram/rom
* Based on block-pair update
* Only RTOS implementation
* Porting to linuxfrom scratch (WIP)

### Demo

...

## Future work

* Finish porting upstream littlefs
* Compilation optimizations: clang, LTO, outline
* Specific workloads tinification (right now only a reference platform)

## References

corstone-700, Cramfs, Littlefs

## Q/A

1. How did you account for swupdate?
   ** You have to take care of provisioning the available 8 MB flash
1. What is the targeted BOM cost?
   ** No comment

Notes:

* cramfs supports partial compression for XIP: data compressed, text not
* being added to meta-arm (Yocto)


