

## Translation
- The kernel needs to **translate** the virtual memory address into a physical address
- The two main solutions include
	1. [[#Paging|Paging]]
	2. [[#Segmentation|Segmentation]]


### Paging
- Virtual memory is divided into regions called **pages**
	- Each page is a **fixed size**, a popular size is *4 KB* but modern OS has bigger sizes as well
- Each page is **mapped** to a physical memory's **page frame**
	- Each **page frame** is the same size as a page
- This mapping is configured and done **by the kernel**. 
	- The kernel maintains a **page table** (one for each process) that maps a virtual page to a physical page frame
- **Most OS** uses this way to translate

For example, if the program does a memory operation like:
```c
int *ptr;
*ptr = 10;
```

The kernel will have to:
1. Find out **which page** the `ptr` is on the virtual memory
2. For that page, find out **which page frame** the page is on the physical memory
3. **Redirect** the access to the correct physical address

A virtual memory address contains the **page number** and the **offset** into the page. 
- There are **more possible** **virtual** pages than there are **physical** page frames
- The kernel does **not map** all pages at once, only when needed at runtime

Paging sizes
- If page number uses $n$ bits, the maximum number of pages is $2^{n}$
- If offset uses $m$ bits, the maximum page size is $2^{m}$

> [!example] Paging Example
> For example, if there are 4 pages, each one having 16 bytes of memory:
> - To enumerate through 4 pages, we need **2 bits**: `00`, `01`, `10`, `11`
> - To enumerate through 16 bytes in a page, we need **4 bits**: `0000`, `0001`, `0010`, ...
> Therefore, we can have a **6-bit** virtual address
> - Address `100101` means page `10` on the byte `0101`
> - Address `000010` means page `00` on the byte `0010`


### Segmentation
- Memory is divided into **segments**. Each segment is:
	- located in the **physical memory**
	- **not of a fixed size**, but a region in the memory

| Address Space  |
| -------------- |
| Kernel         |
| Stack          |
| Memory Mapping |
| Heap           |
| BSS            |
| Data           |
| Text           |

- Each component of the program's **address space** is a segment
	- e.g. text segment, data segment, heap segment

An issue with segmentation
- When freed spaces are **broken up** into different places, **external** **fragmentation**
- When we don't have a contiguous space **large enough** for a new segment, we will waste space in the middle

Paging, however, will not see this issue since **all pages are of the same size**
- It can see **internal fragmentation** instead
- There may be padding bytes at the end of each page
