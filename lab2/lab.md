# lab2

Deliverable is a Xilinx FSBL loaded with the ADCS HIL PL bitstream, as well as the U-Boot second stage. Be able to access the FSBL debug output and U-Boot command line. This will be booted from SD.

### Procedure
1. Acquire the FSBL from Xilinx.
2. Obtain board-specific hardware config. This will also include the PL bitstream and hardware config.
3. Build FSBL (`fsbl.elf`).
4. Build U-Boot (`u-boot.elf`).
5. Generate boot image with Bootgen (`BOOT.BIN`).
6. Copy onto SD card and boot. Verify PL logic and use U-Boot terminal.

### 1. FSBL files

Cloned  `embeddedsw` repo from Xilinx into `bootlin-pynqz1/lab2`. Relevant files from here are in `external/embeddedsw/lib/sw_apps/zynq_fsbl`. Created a symbolic link inside of `lab2`: `ln -s ../../external/embeddedsw/lib/sw_apps/zynq_fsbl lab2/fsbl/source`.

### 2. PL bitstream and hw config

Pulled the `adcs_hil_hw_top.bit` from the old (broken??) x86 64 VM. `ps7_init_gpl.c`/`.h` were pulled from a PYNQ-Z1 repo.

### Build FSBL
