# lab 3 - Kernel

### Architecture

<img width="449" height="351" alt="image" src="https://github.com/user-attachments/assets/b521129a-57ab-4bfb-8ad3-21d5c0dfbfa0" />

### Interfacing with the kernel

System calls are wrapped by the C library. Userspace apps usually never make a system call directly but rather use the corresponding C library function.

### Kernel Sources

Kernel sources can be found [here](https://kernel.org/pub/linux/kernel) as full `.tgz` files and as `patches` (differences between two kernel versions).

Here is an approximate breakdown of space in a given kernel version:

<img width="692" height="203" alt="image" src="https://github.com/user-attachments/assets/4e39eba8-09f5-4b21-9554-719f0368efc9" />

### Kernel Configuration



