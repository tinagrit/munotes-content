Lecture 11

## The storage
The storage is a **persistent** or **non-volatile** (*hold data with no power*). It is cheaper and can store a lot more than [[1_Memory#The memory|the memory]], but it is also a lot slower.

### Spinning hard drives
Historically, the storage has been mostly spinning hard disks. These disks are coated with **magnetized** material to **represent a bit**. 

The read/write head floats above the spinning disk. It can either **detect** or **change** the magnetic orientation. 

A spinning hard drive has:
- **high latency**: it can only read/write when the disk spins so that the specific data is on the head
- **low bandwidth**: it can only read/write data as fast as the disk spins

![[Screenshot 2026-07-14 at 11.25.03 PM.png|400]]

### Solid state drives
SSDs use *NAND* flash storage which is **randomly addressable**, and both **lower latency and higher bandwidth** than spinning disks.

SSDs bandwidth and latency can depend on the **connector**. 
- A traditional storage connector **SATA** has a maximum bandwidth of 600 MB/s
- A faster data transfer connector **NVMe** has a theoretical max bandwidth of 16 GB/s, but 2.6 GB/s is more realistic for drives

While SSDs are a lot faster than spinning hard drives, it is still **a lot slower** than memory.

![[Screenshot 2026-07-14 at 11.34.02 PM.png|400]]

### Network storage
Operating systems can **mount** network disks (any persistent storage over a network) and users/programs **can use them** like local storage.

Network storage can be shared **among many users**, and be larger and faster since dedicated storage devices can hold many drives that combine bandwidth.

Latency and bandwidth will be limited by the drives and the network.


---
## Disk cache
The registers [[1_Memory#Cache|cache]] recently used data from the memory. Similarly:

When a file in disk is frequently or recently used, the operating system can **keep it in memory**. How much data is cached will depend on the operating system.

Linux, for instance, is particularly aggressive. It will use **any free memory** to cache data from storage. For example:

```shell
$ free -m
       total   used   free  shared  buff/cache  available
Mem:   32021   4426   5521     127       22072      27104
Swap:  33742      3  33739
```

In this Linux system, there is 32 GB of physical memory, of which 4 GB is used by programs, and 22 GB used for disk cache. It says on the last column that 27 GB is **available**, since disk cache can be purged.

Some SSDs on the market also have **their own built-in memory** for caching, invisible to the OS but makes reading/writing faster.

