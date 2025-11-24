

## Pipes
- Passes data between programs
- In shell, using symbol `|`

For example:
```shell
$ ls -l | grep "txt"
-rw-r--r-- 1 cmpt201 cmpt201   223 Nov 16 16:26 CMakeLists.txt
```

This passes the output of `ls -l` into `grep` to search for files that include `txt`.

This can be done in C as well. Pipes:
- use a **buffer in kernel**
	- The buffer size is **fixed** in `PIPE_BUF`, which is `4096` in Linux
	- When writing things to pipes, it is only **atomic** if `n <= PIPE_BUF`
- are **unidirectional**, the sender is always the sender, and the receiver is always the receiver
- are a **byte stream**, sending one byte at a time

### Creating a pipe
`pipe` synopsis:
```c
#include <unistd.h>
int pipe(int filedes[2]);
```

Creating a pipe creates **file descriptors**, therefore regular file I/O works, such as `read()`, `write()`, `fprintf()`, `fscanf()`.

In the function prototype, `filedes` is an array of file descriptors, to be returned by `pipe()`:
- `filedes[0]` is the **read end**
- `filedes[1]` is the **write end**

### Use case
- Mostly used for **parent-child** communication
	- Signals don't send any data, just that something happened
	- Return values are only given when a child finishes
- A two-ended pipe is created before calling `fork()`
	- `fork()` **copies** the file descriptor created by `pipe()`, so both the parent and child can use to communicate
- Each process **takes an end** (one for reading end, one for writing end), and closes the one they don't use
	- After closing the writing end, the `read()` will return 0 (EOF)
	- The writing end can "signal" the reading end that it is **done** writing

### Redirecting to a pipe
`dup2` synopsis:
```c
#include <unistd.h>
int dup2(int oldfd, int newfd);
```

`dup2` adjusts the file descriptor `newfd` to point to **the same file descriptor** as `oldfd`.

For example, if we call:
```c
dup2(filedes[1], STDOUT_FILENO);
```
We would **redirect** everything that is about to be sent to the terminal, to `filedes[1]` (write end of the pipe) instead.

### Running a program with pipes
`popen` and `pclose` synopsis:
```c
#include <stdio.h>
FILE *popen(char *command, char *mode);
int pclose(FILE *stream);
```

`popen` conveniently:
- `fork()` a child process
- `exec()` the command
- connects the stream to a pipe, if `mode` is:
	- `"r"`: it returns a file stream, connected to the `STDOUT`
	- `"w"`: it returns a file stream, connected to the `STDIN`

