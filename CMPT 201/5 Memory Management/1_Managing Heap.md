Lecture 5

## Managing Heap
The **heap** is a region of the [[1_Virtual Memory#Virtual memory|Virtual memory]] where programs can flexibly **allocate** memory as they need during execution.  

Programs usually allocate memory in **chunks**. For example, program A may need 20 MB for data I, 10 MB for data II, and 15 MB for data III. When program A is finished with one data, it can **free** that specific allocation, and it will become available for other processes to use.

The heap is just a big region of data. The **program break** is the dividing line between the allocated memory and the uninitialized, available memory.

![[chart18.png|500]]

The `brk()` and `sbrk()` functions can change the program break. 
- `brk()` sets the program break to a specific address
- `sbrk()` *increases* the program break by the specified units

Internally, when we call `malloc()` to get a memory allocation, `malloc` calls `sbrk` to increase the program break.

### Fragmented heap
As programs free their heap allocation, the heap could end up in a **fragmented state**, where the free blocks aren't adjacent.

![[chart19.png|500]]

When the next program wants to allocate memory, it is better to use these **free blocks in between** instead of `sbrk()` for more. 

The ***memory allocator*** manages the heap by keeping track of the free blocks. As a program requests for an allocation via `malloc()`, it returns a pointer to the free region of the size it asks for.

We use a **linked list** to keep track of these free blocks.

### Malloc
There is a list of **all free blocks** in the heap. When we call `malloc()` with a size that we want, it [[#Fit algorithms|chooses]] a large enough block from the list. 

That block is **split into 2**, one with the requested size, and one for the rest.

It then returns the pointer to the first block, and this block is now allocated.

The second block is added back to the free list.

![[chart20.png|800]]

### Using linked list
To keep track of all the free blocks, we can use a small ***header*** at the beginning of each block, creating a **linked list** for the blocks in heap.

The header of each block, at minimum, contains:
- `size`: the size of the block (not including the header). For example, if the block is 100 bytes, and the header is 10 bytes, then `size=100` but the block technically takes 110 bytes on disk.
- `next`: the address of the ***next*** free block. For example, the **first** free block's `next` has the address of the **second** free block. The **last** free block's `next` value is `null`. 
- For non-free blocks (allocated blocks), the `next` value is `null`.

The heap holds a `head` pointer that points to the **first** block.

For example, in this heap, the header takes 10 units. The `head` is pointing to the free block at address 0. That free block's size is 25, and is pointing to the next free block at address 65.

![[chart21.png|300]]

*Note*: the header describes the block *above* it.

### Coalescing
When many free blocks are adjacent to each other, we can ***coalesce***, "combine", these blocks into one free block.

For example, in this heap:

![[chart22.png|300]]

The first free block at address 30 is adjacent to the free block at address 65. After coalescing, the heap becomes:

![[chart24.png|300]]

This allows for larger allocation, and a cleaner state of heap overall.

---
## Fit algorithms
A fit algorithm finds a big-enough block to [[#Malloc|split]] and return to the caller when `malloc()` is called.

### First-fit
Traverse through the linked list (start at `head` and keep looking through `next`'s), and pick the **first free block** that is big enough to fit the requested size.
- *Advantages*: easy to implement, fast since no need to search the entire linked list
- *Disadvantages*: beginning of the list polluted with small objects, takes longer to find bigger allocation requests

### Best-fit
Traverse through the ***entire*** linked list, and pick the **smallest free block** that is still big enough to fit the requested size.
- *Advantages*: reduce wasted memory space
- *Disadvantages*: must search entire list, will create small [[#Fragmented heap|fragmented]] free blocks

### Worst-fit
Traverse through the ***entire*** linked list, and pick the **largest free block** in the heap.
- *Advantages*: produce large leftover free blocks
- *Disadvantages*: must search entire list