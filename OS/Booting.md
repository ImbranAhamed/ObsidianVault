[[OS info]] #os
The booting process of a computer involves several steps:

1. **Power-on Self Test (POST)**: When you turn on the computer, the BIOS (Basic Input/Output System) executes a series of tests called POST. These tests check the hardware components like RAM, CPU, and storage devices to ensure they are functioning properly.
    
2. **BIOS Initialization**: Once the POST is completed successfully, the BIOS initializes the hardware components and checks for connected peripherals such as keyboard, mouse, and drives.
    
3. **Bootstrap Loader**: After the hardware is initialized, the BIOS looks for the bootloader, which is typically stored in the Master Boot Record (MBR) or EFI System Partition (ESP) on the storage device. The bootloader is a small program responsible for loading the operating system into memory.
    
4. **Loading the Operating System**: The bootloader loads the necessary files of the operating system kernel into memory. For example, in Windows systems, the bootloader loads the Windows Kernel (NTOSKRNL.EXE), while in Linux systems, it loads the Linux kernel (vmlinuz).
    
5. **Kernel Initialization**: Once the kernel is loaded into memory, it initializes essential system processes and drivers. This includes configuring memory management, initializing device drivers, and setting up the file system.
    
6. **Init Process**: After the kernel initialization, the init process (or systemd in modern Linux distributions) is started. It is the first user-space process and serves as the parent process for all other processes.
    
7. **User-space Initialization**: The init process starts other essential system processes and services, such as networking, user interface components, and system daemons.
    
8. **User Login**: Finally, the system presents the user with a login prompt or graphical login screen, allowing users to log in and access the computer.
    

Each step in the booting process ensures that the computer's hardware and software components are initialized correctly, allowing the operating system to run smoothly.