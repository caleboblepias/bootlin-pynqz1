# lab1 - Introduction and Toolchain

### System Architecture

<img width="688" height="726" alt="image" src="https://github.com/user-attachments/assets/b62417dc-6ddf-455d-a2d5-e17c951f7ea4" />


Software components of Linux can be broken into distinct categories:
 - Cross-compilation toolchain: Compiler that runs on the host machine, generates code for the target machine
 - Bootloader: Started by the hardware, performs basic initialization, loading and executing of the kernel
 - Linux kernel: Contains process/memory management, network stack, device drivers, etc
 - C library: C functions, provides interface between userspace and kernel applications
 - Libraries and applications: userspace stuff

### Dev Setup

Common Host-Target setups include a serial line for debugging pre-Linux boot as well as a networked line for SSH.

<img width="437" height="137" alt="image" src="https://github.com/user-attachments/assets/0f657809-0ef7-4cd6-93e6-b6c2777a1a9c" />

Linux serial communication programs include Minicom, Picocom, Putty, screen, tmux, and more. Picocom will be used for this course.
 - Installation: `sudo apt install picocom`
 - Run: `picocom -b BAUD_RATE /dev/SERIAL_DEVICE`
 - Exit: `[Ctrl][a] [Ctrl][x]`
 - Find serial device: `ls /dev/ttyUSB* /dev/ttyACM*`

### Cross-Compiling Toolchain

Generally not possible/practical to use a native toolchain for embedded devices:
 - Target restricted in terms of storage/memory
 - Target slow compared to host

So, we cross-compile. Build mechanisms typically rely on *architecture tuples* to identify machines. Examples: `arm-linux-gnueabihf`, `arm-none-eabi-gcc`, etc. The tuples are constructed of the following parts:

`<arch><vendor><os><libc/abi>`
1. The architecture name: `arm`, `riscv`, etc
2. Optionally a vendor name
3. Operating system name, or `none` when bare-metal
4. The ABI (Application Binary Interface) and C library

This tuple is used to configure/build software, and to differentiate from the native toolchain:
 - `gcc` -> native compiler
 - `arm-linux-gnueabihf-gcc` -> cross-compiler

The overall flow for cross-compiling an executable is as follows:

<img width="1373" height="235" alt="image" src="https://github.com/user-attachments/assets/af484396-7828-4d18-ba0c-26e45b10782d" />

#### Binutils

Set of tools to generate and manipulate binaries for a specific CPU architecture.
 - `as` assembler
 - `ld` linker
 - `ar`, `ranlib` to generate `.a` archives (static libraries)
 - `objdump`, `readelf`, `size`, `nm`, `strings` to inspect binaries
 - `objcopy` to modify binaries
GNU Binutils can be found [here](https://www.gnu.org/software/binutils/)
