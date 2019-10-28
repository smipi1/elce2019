# Buildroot: What's New? - Thomas Petazzoni, Bootlin

Commits per release peaked in 2016, now stable at 1200 commits / release

Already had:

* 4 releases / year
* 3 month cycles: 2 dev, 1 stabilization

Added:

* LTS
* YYYY.02 releases get one year support
* Security updates, bug fixes
* YYYY.02.x maintenance branch + regular (monthly) point releases

New architecture support:

* RISC-V
* NDS32

Support for new variants

Dropped Blackfin

Support for ...

## Toolchain

* No significant change
* GCC 8.x + 9.x
* binutils 2.32
* uClibc-ng 1.0.32
* ...

## Existing toolchain

* ARM toolchains
* AArch64 BE
* Andes NDS32
* Updates
* Declaring external toolchains from `BR2_EXTERNAL` trees

## Package infrastructures

* Package infrastructures factorize the common logic
* Two new ...
* golang packages
* meson packages

## Download infrastructure

* Git caching

## Package updates and additions

* Addition of Rust (compiler, cargo), LLVM/Clang (not as compiler), Mender, OpenJDK, OpenRC init systems, OP-TREE OS, zillions of Perl / Python modules
* Major SW stack updates: Qt, X.org, GStreamer, Wayland, Weston, Kodi

## Hardening options

* Stack protection options
* RELRO protections options
...

## New targets

`make show-info`

* Parseable JSON

## Reproducible builds

* Automated testing on autobuild.buildroot.org
* `diffoscope` used to identify non-identical items

## Top-level parallel build

* Build several packages in parallel
* Per-package directories
* Not there yet, but progressing

## Runtime tests

* Each test case:
  ** Builds well-defined config
  ** Runs it under QEMU
  ** Runs some tests to verify a feature is working
* Complimentary to autobuilder...

## Tooling improvements

release-monitoring.org Fedora service

* http://autobuild.buildroot.org/stats

Improved developer notifications

Improved search capabilities

* Can now search build results by config symbol

`make <pkg>-diff-config` for kconfig based packages

F2FS / BTRFS images

gettext tiny alternative

## Conclusions

* Very active project
* LTS
* New CPU architectures
* Infra for new build systems
* Git caching
* Packages kept up-to-date


