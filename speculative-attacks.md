# Analysis of Speculative and Traditional Execution Side Channel and Protection Mechanisms - Antonio Gomez, Intel Corporation

## Side channel methods

Collect information about what a system does

Broad group:

* Power
* Sound
* Cache
* Time

Characteristics:

* Deep system knowledge
* Target implementation
* System works as expected

## Timing attacks

Timing Attacks on Implementation of Diffe-Hellman RSA DSS and Other Systems - 1996 - Paul C Kocher

## Speculative execution side channel methods

What's new:

* Innovative methods
* HW/SW interface
* Target speculative execution

Techniques

* ILP: Pipelining
* OoOE: Out-of-order Execution
* Speculative execution

Characteristics:

* Local methods
* No privilege escalation
* Read access

## How are users affected

End-users:

* Run untrusted code: Download binaries, code, browser
* Updates: OS, libs, apps, browser
* Actions: Enable updates, understand risks

Datacenter:

* Varied workloads: Tursted or untrusted code/guests, Shared resources, System load, Process management
* Actions: Enable updates, Perform risk analysis

Developers:

* Broad group: Firmware/uCode, Kernel, VMMs, Libraries, Tools, Compilers, UI, Web, Apps
* Actions: Long standing security practices

## MDS - Overview

3 internal CPU structures:

* MSBDS: Store buffer - Store data during a write
* MFBDS: Fill buffer - Used during L1D miss
* MLPDS: Load port - Loading data from memory / IO

Data from these structures might be speculatively forwarded

A malicious actor might redirect this forwarded data to a disclosure gadget

## MDS - Thread model

1. Run machine specific method: LPx
1. Victim and attacker on same core: LPx+/-1
1. No control over data brought to CPU
1. Bring data repeatedly
1. Small window to extract data
1. Share CPU for an extended time
1. Postprocess

## MDS mitigation - Microcode

x86:

* Instructions are decoded into uops
* uops: What the instruction does
* Large IS, with legacy instructions

Flush CPU structures

* `VERW`
* Software sequences

2 new MSR:

* ...

## MDS mitigation - OS

1. Implement a function that calls `VERW`
1. Invoke on ring transitions
1. Mechanism to enable / disable mitigations
1. `sysfs` to provide info about the system / mitigation:
  ** Not affected
  ** Vulnerable
  ** Vulnerable: No microcode
  ** Mitigation

## Should we improve process isolation?

* Can we improve process isolation to limit resource sharing?
* What's the finest granularity possible to allocate processes?
* Can we define different trust domains?

## Linux core scheduling

* Under development
* Not too different under low contention
* High contention?
* Can it be used for QoS?

## Rendezvous

Improve kernel isolation from user-space

1. If a hyperthread goes to kernel space, the sibling thread can't stay in user space
1. Send IPI to put sibling in spin loop
1. Clear microacvh state

## Validation efforts to ensure process isolation

* Test functionality
* Ensure no resource starvation
* Study run to run variability
* Check unexpected crashes / hangs
* Long reliability tests
* Observe potential ...



