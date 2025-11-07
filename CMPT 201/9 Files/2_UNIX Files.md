

## UNIX I/O Model
- **everything** is a file, including:
	- regular files
	- directories
	- terminal I/O
	- physical devices
	- networks
	- process information
	- etc.

### /proc
- shows **system** and **process** information
	- use `open()` and `read()` to show info
- dynamically populated **by the kernel** in forms of file
- they are **not real files**
- examples include
	- `/proc/cpuinfo` - CPU Info
	- `/proc/meminfo` - Memory Info
	- `/proc/PID/status` - Process info
	- `/proc/PID/fd` - File descriptor info
	- `/proc/PID/task/TID` - Thread info

### /dev
- stores **device files**
- a "**node**" stored in `/dev/`
- some are **real devices**, like a mouse or a disk
- some are **virtual devices**
	- `/dev/null` is a "black hole" of everything written
	- `/dev/zero` provides infinite null characters
	- `/dev/random` and `/dev/urandom` are pseudorandom number generators

### /sys
- shows **kernel internal** information
- could be used to:
	- kernel subsystems
	- control LEDs
	- access secondary processors
	- communicating to accelerometers
	- etc.

A `ioctl` Syscall can be used to:
- do things **outside** of the normal I/O universal model
- for example, changing the speed of a serial port

### Disk Partitions
- file system to **divide disks** into smaller chunks
	- a **file tree**, a system that manages files and directories
	- each one implementing its own file system
	- starts with a root directory `/`
- stored in `/proc/partitions`
- In Windows, for example, partitions are `C:`, `D:`, etc.
- Swap partition used for [[2_Translation#Paging|Paging]], in `/proc/swaps`


---
## I-Node
- **Stat** and **metadata** information associated to a file
- For example, file types, permissions, owner
- There exists a **unique** i-node number associated to a file, and every file has one
	- Identified by an `int`

To find the associated i-node number of a file, use the `-i` flag on `ls`
```shell
$ ls -li
120296 -rw-r--r-- 1 cmpt201 cmpt201   667 Nov  5 15:12 inode.c
```

In this case, the `120296` (first column) is the i-node number.

### Stat function
`lstat()` synopsis:
```c
#inclde <sys/stat.h>
int lstat(char *pathname, struct stat *statbuf);
```

In the function prototype:
- `pathname` is the string containing the path (could be directory or file)
- `statbuf` is a pointer to the `struct stat`, where the information will be stored

```c
struct stat stat;
lstat("/home/cmpt201",&stat);
```

There are multiple attribute information associated with a `struct stat`, for example:
- `stat.st_mode` is the type of the file (directory, regular file, etc.)
- `stat.st_size` is the file size (in bytes)
- `stat.st_mtime` is the last modified time

For example, if we want to use `st_mode` to determine whether the path is a directory:
```c
if (S_ISDIR(stat.st_mode)) {
	printf("This is a directory\n");
} else if (S_ISREG(stat.st_mode)) {
	printf("This is a regular file\n");
} else {
	printf("Other\n");
}
```

Running this code with the above `lstat()` call, we get:
```shell
$ clang inode.c && ./a.out
This is a directory
```

