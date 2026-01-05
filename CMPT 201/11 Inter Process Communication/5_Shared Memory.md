

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

> [!tip] This is different from malloc
> `malloc()` acts similar to `MAP_PRIVATE | MAP_ANONYMOUS`, where a child gets a **copy** of the memory, instead of one that is shared among them. 
> 
> Using `mmap()` with `MAP_SHARED | MAP_ANONYMOUS` will propagate any changes to all shared processes.


### For unrelated processes
- Use a **shared memory object** before calling `mmap()`
	- `shm_open()` creates the object
	- `ftruncate()` sets the size of the object
	- `mmap()` maps the memory

`shm_open` synopsis:
```c
#include <sys/mman.h>
int shm_open(char *name, int oflag, mode_t mode);
```

In the function prototype:
- `name` is any name for the shared memory, known by all participating processes
	- Creates a **file** in `/dev/shm/<name>`
- `oflag`, set to `O_CREAT` when creating a new object
- `mode` sets the permission 
	- see [[1_File Syscalls#Opening a file|mode in open()]]

`shm_open()` returns the **file descriptor** for the shared memory object


`ftruncate` synopsis:
```c
#include <unistd.h>
int ftruncate(int fd, off_t length);
```

Sets the **size** of the memory object. 
- Without specifying the size, it is defaulted to 0.


After using `shm_open` and `ftruncate`, we can call `mmap`:
- Set `fd` to the **file descriptor** from the shared memory object
- Use `MAP_SHARED`
- Do not use `MAP_ANONYMOUS`, the memory object acts like a file that `mmap` can map to
- Set `offset` to `0`

For example,
```c
int shm_fd = shm_open("hello world", O_CREAT | O_RDWR, S_IRUSR);
ftruncate(shm_fd, 128);
mmap(NULL, 128, PROT_READ, MAP_SHARED, shm_fd, 0);
```


---

## Cleaning up a memory mapping

`munmap` synopsis:
```c
#include <sys/mman.h>
int munmap(void *addr, size_t length);
```

`munmap()` unmaps the memory pointed to by `addr`


`shm_unlink` synopsis:
```c
#include <sys/mman.h>
int shm_unlink(char *name);
```

Call `shm_unlink` after calling `munmap`.
- Will **delete the file** from `/dev/shm`
- Processes that have the memory object open still have access to it

