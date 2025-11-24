
> [!fail] This note is incomplete.

## Memory Mapping
- is used for:
	- Loading an **entire file** into memory, instead of calling `read()`/`write()` to file descriptors
	- **Allocating** memory
	- Accessing **memory mapped devices** in `/dev/mem`, devices that pretend to be memory

`mmap` synopsis:
```c
#include <sys/mman.h>
void *mmap(void *addr, size_t length, int prot, int flags, int fd, off_t offset);
```

In the function prototype:
- `addr` is the starting **address** of the new mapping, or `NULL` to let the OS choose
- `length` is the number of **bytes** to map
- `prot` is the memory **protection**
	- `PROT_EXEC`: executable
	- `PROT_READ`: readable
	- `PROT_WRITE`: writable
	- `PROT_NONE`: not accessible
- `flags` refers to `MAP_SHARED` or `MAP_PRIVATE`, and optionally `MAP_ANONYMOUS`
	- `MAP_ANONYMOUS` is only set to **allocate memory**, without a real file being mapped. `malloc()` uses both `sbrk()` and `mmap()`
		- Set `offset` to `0`
		- Set `fd` to `-1`
	- In `MAP_SHARED`, **multiple processes** share the mapping
		- Creating a mapping and `fork()` a child needs the mapping to be shared
		- Changes **propagate** to the real file and to other processes that map the same file
	- In `MAP_PRIVATE`, changes in one process's mapping **do not appear** for other processes
		- Like a read-only file
		- More memory is allocated
		- `fork()` copies memory, but each process has a **private copy**
- `fd` is the open **file** to be mapped
- `offset` is the offset **into the file** at `fd`

`mmap` returns the pointer to the beginning of the new mapping


---

## Sharing a memory mapping

### For related processes
- Create a memory mapping before calling `fork()` to share them
- Use `mmap()` with `MAP_SHARED | MAP_ANONYMOUS`

### For unrelated processes
