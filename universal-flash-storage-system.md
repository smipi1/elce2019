# Overview of Universal Flash Storage Subsystem - Mohammad Faiz Abbas Rizvi, Texas Instruments India PVT LTD*

## What is UFS?

* Managed flash
* Has a controller
  ** Manages Bad-block management, ECC, wear-leveling, etc
* Protocol

## UFS Features

* High-performance serial I/F + low-power
* Marketed as SD / eMMC replacement
* Theoretical bi-directional full duplex @ 1.45 GBps

## Notable

* I/O Speed @ 1.45 GBps (eMMC 400 MBps)
* I/O @ 0.2 ~ 0.4 V
* Random read @ 68000 IOPS
* Max size 16 TB

## System overview

UFS logical view:

* Logical units
* Config structures
* MIPI Unipro
* MIPI M-Phy

## UFS App layer

* UFS SCSI command set based on SCSI Architecture Model (SAM)
* Transactions with fixed len Command Descriptor Blocks (CBD)

## UFS SCSI Commands

* Read
* Write
* Read capacity
* Report LUs - List LUs
* Test unit ready - Check readiness of LU
* Start stop unit - Power management
* Inquiry

## What is a Logical Unit?

* Externally addressable
* Storage entity
* Internal task queue
* LUs inside a IFS device can be flexibly configured
  ** Physical memory, Write protection, Boot, Memory type (default, system code, non-persistent, enhanced), Prio access, RPMB (Replay-protected memory block)
* UFS can have max 32 LUs
* Additionally 4 well-known LUs (W-LUNS)
* Boot: max 2, 1 active

## Linux UFS bring-up

1. Report LUNs + Response
1. N x Read capacity + Response

## Interconnect layer

* `RST_N`
* `REF_CLK`
* `DIN_t/_c`
* `DOUT_t/_c`

`HS_GEARx` Determines max supported B/W

## Power modes (simplified)

1. Active (ActiveICCLevel: 0x0 ~ 0x15)
1. Idle
1. Sleep
1. Power-down: Non-volatile will be lost

## UFS transport layer

* Transaction consist of packets called UFS Protocol Information Units (UPIU)
* Host is the Initiator, device is the Target
* 12B header
* UPIU Structure

## UTP Read transaction

...

## UTP Host Memory Config

* Up to 32 requests at a given time, identified by Task Tags

## Query request

## UFS Descriptors, flags and attrs

## Configure device from user-space

* Generic SCSI block device `/dev/bsg/ufs-bsg`
* Accepts `ioctl()`

`ufs-utils` helps

## U-Boot implementation

* Since 2020.01



