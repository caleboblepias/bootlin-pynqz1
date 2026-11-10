# lab2

Deliverable is a Xilinx FSBL loaded with the ADCS HIL PL bitstream, as well as the U-Boot second stage. Be able to access the FSBL debug output and U-Boot command line. This will be booted from SD.

### Procedure
1. Acquire the FSBL from Xilinx.
2. Obtain board-specific hardware config. This will also include the PL bitstream and hardware config.
3. Build FSBL (`fsbl.elf`).
4. Build U-Boot (`u-boot.elf`).
5. Generate boot image with Bootgen (`BOOT.BIN`).
6. Copy onto SD card and boot. Verify PL logic and use U-Boot terminal.

### 2. PL bitstream and hw config

Pulled the `adcs_hil_hw_top.bit` from the old (broken??) x86 64 VM. 
