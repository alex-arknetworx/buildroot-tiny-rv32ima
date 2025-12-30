# buildroot-tiny-rv32ima
Buildroot for tiny-rv32ima on Machdyne Chinook

Ported Robert Swierczek's C4 C virtual machine using Vlad Tomoiaga's tweaks for riscv32 compilation and reduced memory pool to 64k.
hello.c is included in the buildroot overlay such that a demo c file is available on Chinook at /etc/

On Chinook, simply run at ~#

c4 /etc/hello.c

This repository contains a buildroot overlay, demo applications and makefiles used to build system images for tiny-rv32ima. An emulator (based on [mini-rv32ima](https://github.com/cnlohr/mini-rv32ima)) which can run on the host system is also included.

The makefile contains multiple targets:
-   `images`, which is also the default target
    - builds the kernel, rootfs and device tree binary, placing them in the _images_ folder
- `hibernate`
    - builds the images and then produces a hibernation snapshot which can be loaded on tiny-rv32ima
- `run_emu`
    - starts an emulator with the built images (doesn't rebuild images)
- `clean`
    - cleans everything (including buildroot)
