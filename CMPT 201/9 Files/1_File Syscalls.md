

## File Offset
- **How far into** the file is the data operated
- A **pointer** to a byte in the file. If we call:
	- `read()` will start reading from that point in file
	- `write()` will write over the data from that point in file
- `read()` and `write()` automatically **increases** the offset
	- Next time these functions are called, next part of data is continued
- The entire file is not read at the same time
	- This is a **waste of RAM**
	- A smaller sized buffer is created, reading smaller parts of a file at a time

### File descriptor
- small `int` for file to read and write
- can **change every time** a file is opened
- some of the constant "file" descriptors are
	- `STDIN_FILENO` = `0`, used for terminal input
	- `STDOUT_FILENO` = `1`, used for terminal output
	- `STDERR_FILENO` = `2`, used for displaying error

### Adjusting the file offset
`lseek` synopsis:
```c
#include <fcntl.h>
off_t lseek(int fd, off_t offset, int whence);
```

In the function prototype:
- `fd` is the file descriptor
- `whence` is from where in the file:
	- `SEEK_SET` is the **start** of the file
	- `SEEK_CUR` is the **current** offset
	- `SEEK_END` is the **end** of file (1 byte after all data)
- `offset` is how much to add to `whence`
	- For example, `lseek(myFd, 5, SEEK_SET)` will adjust the offset to 5 bytes past the start of the file

Seeking **past the end** of file is possible. Next write will extend the file.


---
## File Syscalls

File Syscalls are different than file **library functions**
- `stdio` functions are such as `fprintf()`, `fscanf()`, `fgets()`, `fputs()`
- Library functions store **buffer in memory** before sending Syscalls to the kernel

Syscalls use file **descriptors** `int`, but library functions use file **streams** `FILE *`
	- wrapper around file descriptor
	- like file descriptor **plus a buffer** backing it up
	- get stream from file descriptor with `fdopen()`
	- get file descriptor from stream with `fileno()`

The 5 basic syscalls include:
- [[#Opening a file|open]]
- [[#Reading from a file|read]]
- [[#Writing to a file|write]]
- [[#Closing a file|close]]
- [[#Controlling a file|fcntl]]

### Opening a file
`open` synopsis:
```c
#include <fcntl.h>
int open(char *pathname, int flags);
int open(char *pathname, int flags, mode_t mode);
```

`open()` accepts 2 or 3 parameters
- `flags` refers to the **access mode** and **creation mode**
	- `O_RDONLY` - read only
	- `O_WRONLY` - write only
	- `OR_RDWR` - read and write
	- can be bitwise-or'd with other flags, such as:
		- `O_RDWR | O_APPEND` appends at the end of the file
		- `O_WRONLY | O_CREAT` creates a new file if it doesn't exist
		- `O_RDWR | O_TMPFILE` creates an unnamed temporary file
		- `O_WRONLY | O_TRUNC` truncates file when writing
- `mode` sets the file **permission** when creating
	- not when using read only flag (not creating)
	- `S_IRWXU` - user can read/write/execute
	- `S_IRUSR` - user can read
	- `S_IWUSR` - user can write
	- `S_IRUSR | S_IWUSR` - user can read and write

When using `fork()`, it **clones** some opened file descriptors, so that the children also have them

`open()` returns the [[#File descriptor|file descriptor]] or `-1` for failure

### Reading from a file
`read` synopsis:
```c
#include <unistd.h>
ssize_t read(int fd, void *buf, size_t count);
```

`read()` reads from the file descriptor
- Reading starts at the file offset, and will keep reading for `count` bytes
- If file offset is **at or past** the end of file, `read` returns `0` immediately

`read()` is a **blocking call**, and won't return until the operation is done
- When using `read` in the terminal, it waits for the user input
- Use `O_NONBLOCK` when [[#Opening a file|opening]] to make it not blocking. This will return an error instead if it can't be done immediately.

`read()` returns the number of **read bytes**

### Writing to a file
`write` synopsis:
```c
#include <unistd.h>
ssize_t write(int fd, void *buf, size_t count);
```

`write()` writes the values stored in `buf` to the file descriptor
- `count` specifies how long `buf` is
- Writing starts at the file offset, and will keep writing for `count` bytes
- The actual written bytes could be less than `buf` if:
	- insufficient space on disk
	- interrupted by [[1_Signals#Signals|Signals]]

`write()` returns the number of **written bytes**

`write()` is a syscall, so it sends data directly **to the kernel**
- `fprintf()`, however, writes on the **stored buffer** in memory, making it perform better

### Closing a file
`close` synopsis:
```c
#include <unistd.h>
int close(int fd);
```

`close()` closes the file descriptor
- writes any **remaining buffered data** to the file, if we use Library functions
	- `fflush()` **immediately** sends buffered data to kernel, without closing the file
	- `fsync()` forces the kernel to **automatically** flush buffer, or use `O_SYNC` when [[#Opening a file|opening]] the file

### Controlling a file
`fcntl` synopsis:
```c
#include <fcntl.h>
int fcntl(int fd, int op, ... /* arg */ );
```

`fcntl()` manipulates the file descriptor
- can do many things, check out `man fcntl` for more info
- can **modify flags and mode** for the file after it is opened

