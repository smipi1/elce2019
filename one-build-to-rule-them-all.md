# One Build to Rule Them All: Building FreeRTOS & Linux Using Yocto - Alejandro Hernandez, Xilinx

Devices with versatile architectures

## FreeRTOS + The Yocto Project

ARM on QEMU on OE-Core BSP versatile92s (qemuarmv5)

ARM Embedded Toolchain

* GCC
* Binutils
* GDB
* Newlib: Bare-bones C lib for bare-metal / RTOS

Previous work:

* Newlib + Libgloss on OE-Core
* tclib-newlib (TCLIBC)

Create layer: Meta-FreeRTOS

* Create Distro
* Application is the OS
* BSP vs Application
* Use a class to simplify workflows and create abstractions
* ...

```
DISTRO = "freertos"
DISTRO_NAME = "FreeRTOS"
...
```

## Class: freertos-app

...
DEMO
...

## Multiconfig builds

You can use a single bitbake ...

File-system hierarchy: multiconfig directory

Gets complicated with multiconfig build dependencies

## Future work

* Multiconfig optimisations
* Support more Archs / Ports on Meta-FreeRTOS
* Fine-tuning Meta-FreeRTOS
...

## Takeaways

* Yocto provides scalability
* FreeRTOS just a test-case
* Support more OS/App
* Unify workflow
* Produce an SDK
* Control over toolchain / reproducibility

