

## OS Stack
- Data structure used **by the CPU** to run programs
- Stacks go from bottom up
- An OS stack includes hardware, kernel, and applications.

| OS Stack                        |
| ------------------------------- |
| [[#Applications\|Applications]] |
| [[#Kernel\|Kernel]]             |
| [[#Hardware\|Hardware]]         |

Hardwares can be emulated using [[#Virtualization|Virtualization]]

---
## Hardware
- Physical components
- The two **most fundamental** are the processor (**CPU**, *Central Processing Unit*) and the memory (**RAM**, *Random Access Memory*)
- These components, along with other I/O (*Input Output*) devices, are connected via the **motherboard**

### CPU Speed
- Individual core **clock speed** growth has been **stagnant** recently, since faster clock speed means a lot more heat to manage with
- Instead, CPU gets faster every year due to their cores running **in parallel**
	- softwares being fast or slow is **dependent** on their ability to utilize multiple CPU cores
- Therefore, when we count the number of **transistors** in a CPU, it still grows **exponentially**.
	- **Moore's Law** observes that the number of transistors in an integrated circuit **double every 2 years**

![[Screenshot 2025-10-14 at 2.18.51 PM.png|500]]
<span style="display:inline-block;width:100%;text-align:center;font-style:italic;">Number of transistors (yellow) is a straight line on a logarithmic scale, indicating an exponential growth</span>

### Memory Hierarchy
- Since CPUs get so fast, the RAM needs to **keep up with its speed** so that the CPU is supplied the data it needs when it wants. However,
	- RAM is **much slower** than the CPU
	- RAM is **physically far away** from the CPU
	- Speed of light **limits the speed** in which RAM can transfer data
- This is solved by:
	- **Registers**, a small memory inside of CPU itself.
		- 4 bytes (32 bits) for a 32-bit system
		- 8 bytes (64 bits) for a 64-bit system
	- **Caches**, saving data close to the CPU in case of a quick reuse
		- **L1** (*512 KB*) and **L2** (*8 MB*) caches are private to each core
		- **L3** (*32 MB*) cache is shared among all cores
		- The smaller the cache, the faster it can be accessed
- Since registers and caches hold **so little information**, softwares have to **intelligently** predict which data is needed next, and move it closer to the CPU

| CPU       |
| --------- |
| Registers |
| Caches    |
| RAM       |
| SSD       |
| HDD       |
| Tape      |

### Storing data

> *If registers and caches are so fast, why don't we store everything in the fastest memory close to the CPU?*

- We can't have everything **close to the CPU**
	- If caches are fast so we cache everything, cache **will be slow**
- We can't **afford** large, fast memory
	- Fast memory is very expensive
- We need a **permanent place** to store data
	- Registers, caches, and RAM only store data as long as they are **powered**
	- In case of a power outage, they **lose everything**
	- Data needs to be moved **lower than the RAM**, i.e. SSD, HDD, Tape for it to be stored permanently
- We need a **reliable place** to store data
	- The lower the data is stored (*see chart above*), the more reliable it is.
	- HDD is more reliable than SSD

### CPU Architectures
- Different types of CPUs have different **Instruction Set Architectures** (ISA)
	- Machine instructions that compilers translate code into
	- Two popular ISAs are **ARM** and **AMD64**
- Determines the size of [[#Memory Hierarchy|registry]], which determines the size of **pointers**. In a 64-bit system, 
	- All pointers will be 64 bits.
	- Need 64 physical wires to transfer data to/from CPU and memory

```c
sizeof(char)
// 1
sizeof(int)
// 4
sizeof(char *)
// 8
sizeof(int *)
// 8
```
<span style="display:inline-block;width:100%;text-align:center;font-style:italic;">A 64-bit system</span>


> *Why are most modern systems 64-bit?*

- Using 32-bit systems, all pointers have to be 32 bits. The **total number of addresses** all pointers can point to is:
$$
2^{32}=4,294,967,296 \text{ bytes} \approx 4 \text{ GB}
$$
- This is why 4 GB is the hard limit on RAM for any 32-bit system. With a 64-bit system, the hard limit is **more than we need now**:
$$
2^{64} \approx 17,000,000,000 \text{ GB}
$$


---
## Kernel
- manages access to **resources** and **hardware**
- **controls** all programs that run on the OS
- provides **isolation** and **protection**
	- A user can't access other users' data
	- A program can't interfere with other programs

### Events
- Kernels respond to **events**, they can include
- **Hardware interrupts**
	- e.g. keyboard press, mouse click, network
- **Syscalls**
	- An application calling the kernel
	- e.g. program using `printf()` to ask the kernel to print a message on the screen
- **Signals**
	- A software interrupt that announces an event
	- e.g. `SIGINT` refers to the user pressing CTRL+C, `SIGSEGV` refers to a program's segmentation fault

### Privileges
- **Kernel Mode** (*ring 0*)
	- the OS kernel and drivers (how to talk to a specific hardware) have this privilege
	- full access to hardwares
- **User Mode**
	- all applications have this privilege
	- no access to *privileged instructions*, i.e. certain regions of memory and access to hardware
	- the **root user** (`sudo`) is still in User Mode
		- root has admin privileges, allowing it to run programs and files that normal users can't
		- root has *less privileges* than the kernel


---
## Applications
- User Mode softwares run by the user
- The lifetime of a program includes:
	- A **source code**, original set of instructions
	- gets *compiled* into...
	- An **executable**, containing machine instructions
	- gets *loaded into memory*, becoming...
	- A **running program**

> [!tip] Note
> A program **must be in the memory** (RAM) in order to be run by the CPU. The CPU cannot access bytes without it being in the memory.

### Types of programs
- **Compilation**
	- A compiler compiles a source code directly into a **machine instruction** for the specific architecture
	- is not portable, an executable created on ARM machines **won't run** on AMD64 machines
	- is fast and has better performance
	- e.g. C, C++
- **Interpretation**
	- An interpreter reads and executes the source code **at runtime**
	- is portable, will run anywhere with the specific interpreter installed, e.g. you need Java installed to run any Java program on your machine
	- is slower but easier to debug
	- e.g. Java, Python, JavaScript

### POSIX
- stands for *Portable Operating System Interface*
- **standardizes** how programs can talk to the OS, across different OS
- includes **programming interfaces**, like *file I/O*, *C standard library*, etc.

In C, we can choose the version of POSIX for the set of features we want, for example:
```c
#define _POSIX_C_SOURCE 200809L
```

### ABI
- stands for *Application Binary Interface*
- An **instruction** by the OS telling programs how to do things at the machine level, like:
	- how to call functions
	- how to pass arguments
	- how to return values
- Each OS has **its own ABI**, which is why Windows executable `.exe` won't run on macOS and Linux


---
## Virtualization
- allows programs to be **flexible**, and allows parts of **OS Stacks to swap**
- Mostly used in datacentres
- The **Hypervisor**, or the **Virtual Machine Monitor** (VMM) provides virtualization
	- The VMM runs directly on the Hardware, emulating the hardware for each Virtual Machine

![[Screenshot 2025-10-14 at 3.31.04 PM.png|400]]

### Containerization
- creates a **container**, which is different from virtual machines
- A container includes an **isolated** set of applications and data, but uses the same kernel as everything else
- Docker is an example of a Containerizater

![[Screenshot 2025-10-14 at 3.34.57 PM.png|400]]

