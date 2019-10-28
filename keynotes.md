# Keynotes

## Welcome & Opening Remarks - Jim Zemlin, Executive Director, The Linux Foundation

Linuxfoundation getting more involved in non-software:

ASWF - Academy Software Foundation

Requests to move Open Source Software model to other non-software industries.

Open-standards development:

* Open Specifications: GraphQL Foundations
* Open Specifications with implementations: Open Container Initiative
* Open Standards: Joint Development Foundation

Open-hardware:

* OpenPower
* RISC-V
* Chips Alliance

Open data:

* Open Data Licensing: Community data license agreement
* Open Data Practices: Datapractices.org
* Open Data Sharing: LFENERGY OEDI
* Industry Data Utilities: LFENERGY OEDI

Announcements:

1. New Linux Foundation family member: OpenJS foundation
1. New legal initiatives: Open Innovation Network Pivot
1. New project to improve the Linux kernel: KernelCI

## Robin Bender Ginn, Executive Director, OpenJS Foundation

Open and neutral home for growth
Governance model gives strong voice to projects
Policies prioritize stability and openness
Node.js professional certification program

Want to do more:

* Grow pool of resources for communities we rely on
* Diversify OpenJS communities and leaders
* Improve on security and trust

## Keith Bergelt - Legal initiative update "OIN Pivot"

GNOME foundation was attacked by a patent troll:

* Rothchild (Bad player)
* Community is much more mature. The legal network deals with this as "business as usual".

Looking to come together and collaborate with two large companies to invalidate poor patent.

Strategy pivoting from agressive practicing antagonists to non-practicing entities.

## Kevin Hilman, Co-founder, KernelCI in conversation with Greg Kroah-Hartman, Linux Kernel Developer and Fellow, The Linux Foundation

KernelCI is a project for testing the kernel. Effort to open up the infrastructure and tools around kernel testing.

Governance helps to create a neutral place to allow companies to share.

Wishlist:

1. Sharing code and results.
1. Mining historical data.

Provide a baseline for what is stable. Provides confidence to companies picking their next product kernel.

Tools / infrastructure is open to duplicate and use within company. Ability to not share results until e.g. product is shipping.

## MDS, Fallout, Zombieland & Linux - Greg Kroah-Hartman, Linux Kernel Developer and Fellow, The Linux Foundation

MDS:

* Same family of bugs as Spectre / Meltdown
* Hardware
* Exploiting speculative execution model
* Many variants
* Will linger a very long time
* More teams finding these bugs: Finding them by reading patents
* One program can read another programs data
* Crosses VM boundairies
* OpenBSD was right: Disable SMT

RIDL:

* Rogue-Inflight-Data-Load
* CPU Line-gill buffers and Load ports

Fallout:

* Exploits CPU Store Buffers
* Breaks ASLR
* Meltdown made it easier to exploit

Zombieland:

* Exploits CPU Line-Fill buffers
* Much like RIDL

Other variants:

* ...

SWAPGS

* Found reading patents
* 1 - 5% performance hit

Flushing CPU buffers is slow:

* Mitigation only possible by disabling SMT and updating kernel and BIOS
* Numbers depend on workload
* Kernel build: -2% smt=on, -15% smt=off (heavily multi-threaded, CPU bound)

Do you feel lucky?

* You need to choose: security or performance
* What choice did your cloud provider make?
* https://make-linux-fast-again.com/
  ** 20% faster builds

Linux response:

* Fixes by announcement date
* Intel notified devs in advance
* Process needs to improve: Debian only notified 48 hours before release
* More fixes after announcement
* Update your kernel and BIOS

Linux security fixes

* At least once a week
* Indistinguishable from other bugfixes
* Few CVEs assigned for kernel bugs

Linux LTS Kernels fix problems

* Bugs fixed before you realize it is an issue

"If you are not using a supported Linux distro kernel, or a stable / longterm kernel, you have an insecure system"

Your talk is sad:

* Hardware has bugs
* Linux fixes those bugs before you realize it
* Disable hyperthreading (SMT) for now
* Always update kernel / BIOS and all is well

## Open Source, Better, Faster, Stronger - Kelly Hammond, Senior Director of Engineering, Intel Corporation

* We know Linux developers, because we are Linux developers.
* Deep connection to open source.
* Making performance that matters.
* Performance in a data driven world.
* Need more data available with lower latency.
* Faster access to more data with persistent memory.
* Vector Neural Network Instructions.
* Going fast together:
  ** Create a beat: Automated development model with daily releases.
  ** Optimize the full stack.
  ** Deliver
* Stacks: https://clearlinux.org/stacks
  ** Deep learning reference stack v4
  ** Data analytics reference stack
  ** Database reference stack
* Extended analytics use cases
* Stronger: Making records
* Consistent leading Linux OS performance
* End-to-end performance stacks
* Experience performance

## The Cost of Democratization? Open Source and the Future of Ethical Use - Dr. Rumman Chowdhury, Global Lead for Responsible AI, Accenture Applied Intelligence

Better Language Models and Their Implications: GPT2

How can we ceconcile:

* Culture of open source recolutionized how we adopt and utilize tech
* Power of democratized tools helps deconstruct centralized power
* Rapid democratization is what leads to a level playing field

How do we stop malicious actors? Can we? Is it our responsibility?

What pre-existing work can we learn from?

* Biomedical
* Nuclear
* Infosec
  ** Responsible disclosure

Shortcomings

* Institutions are lacking
* Regulation leads to recentralization
* Industry culture is built on easy to adopt / use tools and software

What is responsible release?

* We have no idea?

Thoughts on how to start?

* Law and Adverserial Machine Learning - Kumar 2018
  ** Benchmark attacks and defenses
  ** Architect for forensics
  ** Take into account civil liberties

Benchmarking

* Shostack's DREAD framework for threat modeling:
  ** Damage
  ** Reliability of attack
  ** Ease at which an attacker cna exploit / launch attack
  ** Scope of affected users
  ** Ease at which attacker can Discuver the Attack

Forensics

* Datasheets for datasets, model cards
* PAI initiative in ABOUTML
* Explainability, traceability

Civil liberties

* Dual use of ML models
  ** Infamous gaydar paper
* Facial recognition
* Surveilance tech used to stifle dissent movements

We are in an era of massive impact, massive growth and massive potential


