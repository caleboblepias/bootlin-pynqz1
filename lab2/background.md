# lab2 - Boot process and bootloaders

The bootloader performs:
 - basic hardware init
 - Loading of an application binary (generally the kernel here) from flash, network, or some other form of non-volatile storage
 - Execution of the application

Most bootloaders provide a shell or menu - commands to load data, inspect memory, etc. The bootloader is the first piece of code running by the processor that can be modified by developers.

### ROM code

Most embedded platforms include ROM code whose behavior is described in a datasheet. It is responsible for finding a suitable bootloader, loading it, and running it. The source can be selected (usually as a jumper or pin state) as NAND/NOR flash, USB, SD, eMMC, etc. Typically runs with the external RAM not initialized, so it can only load the bootloader into internal SRAM. This restricts the size of the bootloader, and forces the boot process to be split into two steps:
1. First stage bootloader (runs from SRAM, inits external DRAM)
2. Second stage bootloader (larger, runs from external DRAM)

