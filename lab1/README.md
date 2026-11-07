# lab1 - Introduction and Toolchain

## System Architecture

<img width="688" height="726" alt="image" src="https://github.com/user-attachments/assets/b62417dc-6ddf-455d-a2d5-e17c951f7ea4" />


Software components of Linux can be broken into distinct categories:
 - Cross-compilation toolchain: Compiler that runs on the host machine, generates code for the target machine
 - Bootloader: Started by the hardware, performs basic initialization, loading and executing of the kernel
 - Linux kernel: Contains process/memory management, network stack, device drivers, etc
 - C library: C functions, provides interface between userspace and kernel applications
 - Libraries and applications: userspace stuff
