

## Making a new process
- During a program execution, we can use **Syscall** to **create a new process** to run along with the current process
- Each process has its own **isolated address space**
	- Pointers in one process **cannot** access memory in the other
	- Modifying a variable value in one process **does not** affect variables in the other
	- Two processes can communicate **only through the OS**, and if both processes agree to

If the initial process (**parent**) wants to make new processes (**children**), there are 2 steps in Linux.
1. [[#Fork|Fork]] - Create a new process
2. [[#Exec|Exec]] - Run a different program
The parent can use [[#Wait|Wait]] to find out when a child process is finished.


### Fork
`fork()` synopsis:
```c
#include <unistd.h>
pid_t fork(void);
```

A syscall and a [[1_OS Stack#POSIX|POSIX]] function to ask the OS to **create** a new process
- creates an **identical copy** of the parent process that calls it
	- The child process will execute the **remainder of the code** that exists in the parent process after `fork()`

For example, consider:
```c
int main() {
	printf("Hello\n");
	fork();
	printf("World\n");
	return 0;
}
```

```
Hello
World
World
```

The line `printf("World\n");` is run twice
- The first time by the parent
- The second time by the child

`fork()` returns a **process ID** (PID, `pid_t`)
- For the **parent**, the returned `pid` will be the process ID of the child, or `-1` on failure to fork
- For the **child**, the returned `pid` will be `0`

For example, consider:
```c
int main() {
	pid_t pid = fork();
	if (pid == 0) {
		printf("I am the child. My PID is %d. ",getpid());
		printf("My parent's PID is %d.\n",getppid());
	} else if (pid == -1) {
		printf("fork() failed\n");
	} else {
		printf("I am the parent. My PID is %d.\n",getpid());
	}
	return 0;
}
```

```
I am the parent. My PID is 20311.
I am the child. My PID is 20312. My parent's PID is 20311.
```

Now, we are running **different code** for different processes
- The child process has `pid==0` and will only print its respective statement
- `getpid()` returns the PID for the process it is running in. 
- For any child process, `getppid()` returns the PID for the parent that forked it

> [!tip] Note
> A **fork bomb** is a code that repeatedly keeps calling `fork()`. Since child processes will be created exponentially, this can overwhelm the processing unit, and can be an attack called DoS (Denial of Service).


### Exec
`exec()` synopsis:
```c
#include <unistd.h>
int execl(char *path, char *arg0, ..., NULL);
int execle(char *path, char *arg0, ..., NULL, char * envp[]);
int execlp(char *file, char *arg0, ..., NULL);
int execv(char *path, char * argv[]);
int execvp(char *file, char * argv[]);
int execvpe(char *file, char * argv[], char * envp[]);
```

A syscall and a **family** of [[1_OS Stack#POSIX|POSIX]] functions to replace the current process with another task
- **removes** the current running program from the process memory
- **loads** a new program into the memory
- **starts executing** the new program

For example, consider:
```c
int main() {
	printf("Hello\n");
	fork();
	exec(...);
	printf("World\n");
}
```

```
Hello
```

The `exec` removes the current process for both the child and the parent, and the second `printf` never gets run.

Usually, we want to replace the **child's process** so that it can run something else. We would do:
```c
int main() {
	pid_t pid = fork();
	if (pid == 0) {
		exec(...);
	} else if (pid == -1) {
		printf("fork() failed\n");
	}
	// continue on with parent
	return 0;
}
```

As mentioned that `exec()` is a **family of functions**, the "types" of `exec()` are:
- **Arguments**
	- `l`: passing in each argument individually, ending with a `NULL`
		- for example: `ls -l -a` will be passed in as 
		  `execl("/bin/ls", "/bin/ls/", "-l", "-a", NULL);`
	- `v`: passing in arguments as a `NULL` terminated array
		- for example: `ls -l -a` will be passed in as
		  `char* args[] = {"/bin/ls", "-l", "-a", NULL};`
		  `execv("/bin/ls", args);`
- **Path**
	- `p`: to let Linux search the path for the program, similar to the terminal, for example:
		- without `p`: `ls` will be passed in as
		  `execl("/bin/ls", "/bin/ls", NULL);`
		- with `p`: `ls` will be passed in as
		  `execlp("ls", "ls", NULL);`
- **Environment**
	- `e`: to include the specific environment variables

> [!tip] Note
> The first argument is always the program itself.


### Wait
`waitpid()` synopsis:
```c
#include <sys/wait.h>
pid_t waitpid(pid_t pid, int *_Nullable wstatus, int options);
```

> [!tip] Note
> `Nullable` means it **can** be `NULL`, but it doesn't have to be.

A syscall and a [[1_OS Stack#POSIX|POSIX]] function to find out when a child process is finished
- waits on a child process's **termination**
- obtains the child's **status**

In the function prototype:
- `pid` refers to **which child** to wait. `-1` will wait for **any child**.
- `wstatus` refers to an integer that the **exit status** of the child will be stored in. If we don't care, we can pass in `NULL`. Parent can call:
	- `WIFEXITED(wstatus)` will return `true` if the program exited normally and `false` if there was an error
	- `WIFSIGNALED(wstatus)` will return `true` if the program exited due to a signal call, e.g. a `SIGINT` (CTRL+C) 
- `options` allows us to specify options on waiting.
	- `0` will make it a **blocking function**, execution will continue when the child exits
	- `WNOHANG` will make it a **non-blocking function**, `waitpid` will not wait


---
## Errno
```c
#include <errno.h>
errno
```

- A **global variable** to keep track of syscalls and functions when there is an error
- Similar to `wstatus` from `wait()`

For example:
```c
if (errno == EINTR) {
	perror("error");
}
```

This will catch an error where a syscall has been **interrupted by a signal** call.

