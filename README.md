# basic-kernel
A basic kernel with a loader and a linker. The kernel only prints "Hello World" on execution.

It is advised not to run on bare metal system since the code is not polished for it. For the execution of this project, use hypervisors such as Oracle VirtualBox, QEMU, GNOME Boxes and others. The following project contains 4 files:
- Kernel.cpp : The kernelMain function is the entry point of the kernel code, which is invoked by the bootloader after loading the kernel image. This function currently calls the printf function with the string "Hello World!", which writes the string to the text-mode video buffer at memory address 0xb8000, causing the string to be displayed on the screen.

- linker.ld : The code block is a linker script used to organize the different sections of an operating system kernel image in memory. It specifies the entry point of the kernel, the output format and target architecture, and defines the text, data, and BSS sections, as well as the constructor function table used to initialize global objects and variables. It also discards unnecessary sections such as finalization functions and comments.

- loader.s: It is assembly code that defines a bootloader for a multiboot-compliant kernel. It sets up the multiboot header by defining the magic number, flags, and checksum, and then declares the bootloader entry point as the global symbol "loader".

- makefile: This is a makefile that builds an operating system kernel image from C++ and assembly source files. It uses the GCC C++ compiler, the GNU Assembler, and the GNU linker to compile and link the source files. The resulting binary file is named mykernel.bin, and it can be installed to the /boot directory using the install target. The makefile specifies various compiler and linker flags, and it defines rules for generating object files from C++ and assembly source files.
