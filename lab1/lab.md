# lab1

Deliverable is to create an executable for the ARM64 Ubuntu Linux VM using the `glibc` standard C library, `aarch64-linux-gnu` GCC toolchain, and binutils. The diagram outlining the toolchain process will be followed fairly closely.

### Verify C standard library

`ldd --version` returns `ldd (Ubuntu GLIBC 2.43-2ubuntu2.4) 2.43`. We aren't using any kernel headers here, but 

### Kernel header awareness

`printf` actually uses `write` system calls under the hood, but this is outside the scope of this lab. This will be explored more deeply in the application code devlopment labs. 

### GCC

#### Preprocessing

`gcc -E hello.c hello.i`

#### Compilation

`gcc -S hello.i -o hello.s`

### Binutils

#### Assembler

`as hello.s -o hello.o`

#### Linking

`gcc -v hello.o -o hello.elf`

### Run

`./hello.elf`

<img width="373" height="28" alt="image" src="https://github.com/user-attachments/assets/daf37ec7-9c78-4709-bc24-34b38dc7990a" />
