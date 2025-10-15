

## Memory
- Computers work **mainly with** memory
- Most machine instructions are calls to **read or write** from/to memory
- Knowing the memory address, all addresses in the RAM (Random Access Memory) are **equally fast** to access

### Assigning memory
- In the early days, memory assignment is given to programs as a **fixed range** in memory. Problems include:
	- Each program could only use that **small amount** of memory. Larger programs use the same amount as smaller programs
	- No protections against one program **accessing memory of another** program


---
## Virtual memory
- Unlike assigning a fixed range, virtual memory mechanism:
	- allows for each program to have its own **memory space**
	- protects and **isolates** each program's memory access
- A process will **use the virtual memory** instead of directly using the physical one
	- process is given a virtual space (**abstraction**)
	- Pointers in the virtual space range from $0$ to $2^{64}-1$ (in a 64-bit system)
	- The OS can **translate** where that is in the physical memory
- Only **kernel level** components have access to both virtual and physical addresses

| Address Space  |
| -------------- |
| Kernel         |
| Stack          |
| Memory Mapping |
| Heap           |
| BSS            |
| Data           |
| Text           |

These address spaces are **unique** to each process running on the machine.


### Locality
- At any given point, a program is very likely only accessing **a small part** of its memory space
- Two types of locality **predicts** what data the program will soon need
	- **Temporal Locality** - Variables or data structures are usually accessed repeatedly.
	- **Spatial Locality** - The next data the program needs is likely *near* the previous data.
- Data that the OS thinks we **don't need soon**, can be **swapped** onto the SSD to free up memory for other processes.
	- The file swapped on the SSD is called the **Swap Space**

