Prerequisites
Before starting, you should have a good understanding of:

C Programming: OS/161 is written in C, so you should be comfortable with low-level programming.
Computer Architecture: Understanding how a computer's hardware works, especially the CPU, memory, and input/output systems.
Systems Programming: Knowledge of system calls, processes, virtual memory, and interrupt handling.
Assembler: Some basic assembly for low-level interactions.
Compilers: Understanding how compilers work, as OS/161 uses GCC to build the kernel.

1. Set Up the Environment
The first step is setting up a development environment that includes the following:

Virtual Machine (VM): OS/161 runs on a simulator, so you’ll need to install the sys161 simulator.
Cross-Compiler: You’ll need to install a cross-compiler (like GCC) to build the OS.
Debugger: Set up a debugger (e.g., GDB) to inspect your kernel.
Text Editor/IDE: Choose your preferred text editor/IDE for coding (e.g., Vim, VSCode).
bash
Copy
Edit
sudo apt-get install build-essential
sudo apt-get install sys161
Download the OS/161 source code from the official repository or as per your course materials.

2. Understand the Structure of OS/161
OS/161 is divided into two main components:

Kernel (os/161): The core of the OS, managing processes, memory, files, and hardware.
User-Level Library (lib/): Provides functions to interact with the OS, like system calls.
Familiarize yourself with the directory structure:

kern/arch/arc: Architecture-specific code (e.g., handling CPU and interrupts).
kern/include: Header files that define structures, constants, and function prototypes.
kern/main.c: Entry point of the kernel.
kern/console.c: Console I/O functions.
kern/syscall.c: System call implementation.
3. Start with Bootstrapping the Kernel
The first thing OS/161 does is boot the system. The boot process loads the kernel into memory and prepares it to run.

Bootloader: Understand the sys161 bootloader, which sets up memory, loads the kernel, and transfers control to the kernel.
Kernel Initialization: The kernel needs to set up the system's resources. This includes:
Setting up exception handlers
Initializing CPU structures
Setting up the memory management unit
4. Memory Management
Memory management is a fundamental part of an OS. Start by implementing:

Memory Allocation: You need a way to allocate and free memory. Implement a simple memory allocator like a buddy allocator or bitmap-based allocator.
Page Tables and Virtual Memory: Implement the virtual memory system, where the kernel uses page tables to map virtual memory to physical memory.
Process Address Space: Set up a process's virtual address space, and manage the kernel and user memory regions.
5. Implement Processes and Scheduling
A fundamental part of an operating system is process management. In OS/161, this can be divided into:

Process Creation: Implement the basic process structure (PCB - Process Control Block) and create processes. The first process that runs is usually the init process.
Context Switching: Implement the logic for saving and restoring process states during context switches (interrupts, system calls).
Scheduler: Implement a round-robin or priority-based scheduler to select which process to run.
Interrupt Handling: When an interrupt occurs, you need to save the current process context, switch to an interrupt handler, and then restore the context afterward.
6. System Calls
System calls allow user programs to interact with the kernel. Implement the following system calls:

fork(): Create a new process.
exec(): Load and execute a new program.
wait(): Wait for a process to finish.
exit(): Terminate a process.
getpid(): Get the process ID.
open(), read(), write(): Basic file operations.
7. File System
Implement a simple file system for the kernel. The file system typically includes:

In-memory File System: Implement a basic in-memory file system for storing files and directories.
File Descriptors: Manage file descriptors for processes.
System Calls for Files: Implement basic file operations (e.g., open, read, write, close).
8. Device Drivers
OS/161 also needs to interface with hardware, so you'll need to write drivers for various devices. For instance, you could start with:

Console Device Driver: Handle input/output from the terminal.
Timer Interrupts: Implement a timer interrupt handler to provide periodic clock ticks, which is needed for scheduling.
Disk I/O: Implement basic disk access functions (e.g., reading and writing sectors).
9. Synchronization
Implement synchronization primitives like:

Locks: For mutual exclusion, to prevent race conditions.
Semaphores: For managing access to shared resources.
Condition Variables: For managing process synchronization, e.g., implementing wait and signal semantics.
10. Testing and Debugging
Once you implement these core components, you can start testing your kernel with the provided user programs or write simple test programs. Use sys161 to simulate and run your OS and a debugger (GDB) to step through the code.

11. Gradually Add More Features
After you have implemented the core of the kernel, you can continue to expand the features of your OS by adding:

Networking Support: Implement networking protocols if you want your OS to support networking.
Advanced Scheduling Algorithms: Implement priority-based or multi-level feedback queue (MLFQ) schedulers.
Advanced Memory Management: Implement features like paging with demand paging and swapping.
Final Thoughts
Building an OS like OS/161 from scratch is a big project that requires understanding both theoretical and practical aspects of systems programming. Focus on building each component step by step, ensuring you understand the underlying principles, and test regularly. Additionally, you can consult the OS/161 documentation and various online resources for more detailed instructions.







