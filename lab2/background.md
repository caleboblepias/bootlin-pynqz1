# lab2 - Boot process and bootloaders

The bootloader performs:
 - basic hardware init
 - Loading of an application binary (generally the kernel here) from flash, network, or some other form of non-volatile storage
 - Execution of the application

Most bootloaders provide a shell or menu - commands to load data, inspect memory, etc. The bootloader is the first piece of code running by the processor that can be modified by developers.

### Boot Process

Most embedded platforms include ROM code whose behavior is described in a datasheet. It is responsible for finding a suitable bootloader, loading it, and running it. The source can be selected (usually as a jumper or pin state) as NAND/NOR flash, USB, SD, eMMC, etc. Typically runs with the external RAM not initialized, so it can only load the bootloader into internal SRAM. This restricts the size of the bootloader, and forces the boot process to be split into two steps:
1. First stage bootloader (runs from SRAM, inits external DRAM)
2. Second stage bootloader (larger, runs from external DRAM, optional)

<img width="736" height="566" alt="image" src="https://github.com/user-attachments/assets/cc0fe09d-9c80-4a38-ad19-f1e10ef573cd" />

TRMs typically specify the requirements for boot sequencing for a given SoC. We will be using [U-Boot](https://u-boot-project.org/) as our bootloader of choice; this is used as the second-stage bootloader for the Zynq 7020, with a Xilinx-specific FSBL.

Note: there is a lot of Bootlin content about trusted firmware. This is probably important but will be skipped for now.

### Zynq 7000 Boot Process

<img width="1109" height="137" alt="image" src="https://github.com/user-attachments/assets/30817106-2e17-4d57-a0c9-31404e92b17d" />

1. Stage 0 - BootROM: Executes from internal ROM, reads boot mode, loads FSBL into OCM
2. Stage 1 - FSBL: Executes from on-chip memory (OCM), inits hw (clocks, DDR, etc), optionally programs PL, loads U-Boot
3. Stage 2 - U-Boot: Executes from external DDR, inits boot env, loads kernel
4. Stage 3 - Linux: Executes from external DDR, initializes MMU, drivers, scheduler, memory management, mounts root fs





