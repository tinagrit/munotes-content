Lectures 8, 10-11

> [!failure] This note is incomplete.

## The memory
The memory consists of [[3_Processor#Memory|capacitors that hold charges]]. Essentially, it is an **array of bytes**, and each byte has a **unique address**.

The memory lets us:
- examine a byte at the address: `x = memory[1234]`
- update a value at the byte address: `memory[1234] = x`

If we have a data that takes many bytes, like a 64-bit [[1_Integers#Unsigned Counting|integer]], we can use the memory at byte $n$ to byte $n+7$ to store 8 bytes.

> [!tip] Note
> So far, we've been accessing the memory through [[5_Stack#The Stack|the stack]]. However, the stack is only limited to $\approx 8\text{ MB}$ of data, and a function must give up all of its stack space when it returns. 

### Memory hierarchy
The memory hierarchy describes the spectrum of places data could be stored.

| Places                                                                                                                            |
| --------------------------------------------------------------------------------------------------------------------------------- |
| [[3_Processor#Register\|Registers]]                                                                                               |
| [[#Cache\|L1 Cache]]                                                                                                              |
| L2 Cache                                                                                                                          |
| L3 Cache                                                                                                                          |
| Memory                                                                                                                            |
| [[4_Storage#The storage\|Storage]]: [[4_Storage#Solid state drives\|SSD]]/[[4_Storage#Spinning hard drives\|HDD]]/[[#Swap\|swap]] |
| [[4_Storage#Network storage\|Network Storage]]                                                                                    |


### DRAM
Modern computers use **DRAM** (*Dynamic Random Access Memory*). The **random** refers to the ability to access any part of it in similar time. 

Each bit is held by a capacitor that holds a charge. These only retain data as long as the RAM **is powered**.

DRAM is a different technology than the [[3_Processor#Flip flop|flip flops]] in the registers, which is **SRAM** (*Static Random Access Memory*).

### Pointers
A pointer is a **number** representing the address in memory, usually a 64-bit [[1_Integers#Unsigned Counting|unsigned]] integer. 

In C, the type `int64_t*` is a pointer to an `int64_t`. If we have `int64_t* p`, it is a memory address where the locations $p$ to $p+7$ hold bits that C interprets as an `int64_t`.

Registers like the [[5_Stack#Stack pointer|stack pointer]] (`%rsp`) always holds a pointer to the top of the [[5_Stack#The Stack|stack]].

> [!tip] Note
> In programming languages like C++ and Java, a **reference** is essentially a pointer, but the actual memory **address is hidden**, to prevent pointer arithmetic and accessing data that it shouldn't.

### C Pointer arithmetic
In C, we can do pointer arithmetic by **adding and subtracting** the pointer directly. However, the offset is by the **size of the value** instead of by bytes.

For example, if we have a pointer to an `int64_t`:
```c
int64_t number = 123456;
int64_t* pointer = &number;
```

If we do a `pointer+1`, we would get the memory address **8 bytes** after the address at `pointer`, since `int64_t` takes up 8 bytes.

Basically, adding `i` to the pointer adds `i * sizeof(type)` to the memory address.

---
## Syscalls


---
## Cache
Memory is very slow, compared to registers. Retrieving a value from memory takes **~100 CPU cycles**, which is a lot.

We can use **cache** to mitigate this. We can put a little bit of [[#DRAM|SRAM]] (since it is expensive) between the processor and memory, to **hold** **some data** from the memory. This data can be accessed by the processor **quickly**.

When memory is accessed, a ***cache line*** (64 bytes) will be put in cache. Most code will access nearby memory next, so it will be ready to go.
- If memory access is found in cache, a ***cache hit***, we won't need to touch the DRAM
- If memory access is not found in cache, a ***cache miss***, we will need to access the DRAM

### Levels of Cache
Caches are arranged from **smaller/faster** (*L1*) to **larger/slower** (*L4*). 

Each CPU core has its own L1 for instruction and data, and L2 for data.
The L3 is shared among every cores in the processor.

![[Screenshot 2026-07-03 at 11.26.10 AM.png|450]]

Fetching from L1 takes ~4 cycles, L2 takes ~10 cycles, and L3 takes ~40 cycles. Fetching from memory directly takes ~50 cycles, making the total cache attempt + memory ~100 cycles.

The number of cycles needed is the **latency**, *how long* until the data arrives. (think of the length of a water pipe)

We also need to consider the **bandwidth**, *how much* data it handles at once. (think of the width of a water pipe)

The actual output involving latency and bandwidth is called the **throughput**.

| Storage         | Size       | Latency  | Throughput    |
| --------------- | ---------- | -------- | ------------- |
| Registers       | < kB       | 1        |               |
| L1 Data Cache   | 32 kB      | 4        | 400 GB/s      |
| L2 Cache        | 256 kB     | 12       | 100 GB/s      |
| L3 Cache        | 8 MB       | 36       | 40 GB/s       |
| Memory          | Many GB    | 44       | 13 GB/s       |
| SSD             | Few TB     | 200-600  | 500-5000 MB/s |
| HDD             | Several TB | 10k-20k  | 80-160 MB/s   |
| Network storage | Many TB    | 70k-175k | 1 GB/s        |

### Memory Locality
Accessing memory that is **local** will always be **faster**.

When memory is accessed, values around the accessed memory "64-bit ***cache line***", is put in the cache. This means that the next time we ask for value in memory, if it is **close enough** to the value prior, we only need to access the cache and not the actual memory.

If we allocate an array, all the values in the array will be **next to each other**. If we access the values **sequentially** or close to another value, our program will **run faster** since we are utilizing cache.

![[chart21.png|400]]

If we use a linked list, however, each element can be in a **random place** in the memory, and access to any element will require an actual memory access. This will run **slower** than arrays.

![[chart22.png|400]]

As a programmer, we should keep memory access **local** as much as possible.


---
## Virtual memory
Virtual memory is a level of abstraction **between** the code, and the physical memory.

The memory addresses the programmer sees are not the addresses in the physical memory, but in **the virtual memory**. These addresses are **translated** to physical addresses by the computer's **MMU** (*Memory Management Unit*).

When the program asks the operating system for memory:
- The OS gives the program a **virtual memory space**
- The OS **assigns that space** to some physical memory
- The OS **tells the MMU** which part of physical memory belongs to which process
- The MMU **translates** addresses as instructions run

![[Screenshot 2026-07-14 at 11.43.15 PM.png|350]]

Virtual memory also **prevents** the program from accessing another program's memory. A *segmentation fault* refers to accessing memory outside of the process **segment**.

### Page table
The assignment between virtual memory and physical memory is done **in pages** (1 page = 4 kB in most systems). The MMU has a ***page table*** to map between virtual and physical.

Larger page sizes mean more waste when programs need smaller amounts of memory; smaller pages mean a larger page table.

The **TLB** (*translation lookaside buffer*) is effectively an **in-memory** [[#Cache|cache]] for page table lookups, so that the MMU doesn't have to hit the table every time.

### Swap
Swap allows the computer to have **more virtual** memory than physical memory.

The OS can take data from a virtual memory page, **copy it to** [[4_Storage#The storage|disk]], and remove it from physical memory. The space on disk used for this purpose is called a **swap space**.

![[Screenshot 2026-07-14 at 11.53.59 PM.png|200]]

Essentially, some data on the memory is stored in the disk.

When a program tries to access a page that has been **swapped out** (in disk), the MMU triggers a *major* **page fault**, which tells the Operating System to bring the page back to physical memory. If there is no more physical memory available, another page will have to be swapped out.

While disk is much slower than memory, it is not too bad it this only happens occasionally.

> [!tip] Minor page faults
> When your program requests memory from the OS, the physical memory isn't yours until you access it for the first time. When that happens, a **minor** page fault is triggered and the memory is cleared out.


### Thrashing
If the programs are actively using more data than it will fit in the physical memory, the OS needs to **keep bringing in** new pages.

The process can be too busy trying to swap and program can be **left unexecuted**.