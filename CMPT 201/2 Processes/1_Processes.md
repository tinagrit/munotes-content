

## Processes
- Programs are executable files that are compiled from the source code
- Processes refer to a **running program** in memory

### Executing a program
> [[1_OS Stack#Applications|Recall]]: *A program **must be in the memory** (RAM) in order to be run by the CPU. The CPU cannot access bytes without it being in the memory.*

To start executing a program, the OS will:
- **allocate memory** in the RAM for the instructions
- **load** the machine instructions from the executable onto the memory
- **allocate memory** in the RAM for the data needed (variables)
- **start executing** by making the program a process

### Controlling a process
> [[1_OS Stack#Events|Recall]]: A program can call the kernel using **Syscalls**.

See more [[2_Parent and Child|Parent and Child]]
Important Syscall processes include:
- `fork()` **clones** the current process, effectively making a child process
- `exec()` **replaces** the current process with a new one
- `wait()` **waits** until a created process is finished

> [!tip] Note
> The child/parent processes can be visualized through the Linux tool `btop`.

### Sleep
`sleep()` synopsis
```c
#include <unistd.h>
unsigned int sleep(unsigned int seconds);
```
- puts the process to sleep for `seconds` seconds


---
## Reading the `man` page
- There is a `man` page for each Linux functions and C standard library functions. 
- This can be accessed by `man [function]`

1. The **DESCRIPTION** section explains what the function does. Check if it is what we want. For example,

```
DESCRIPTION
     The strcmp() and strncmp() functions lexicographically compare the null-
     terminated strings s1 and s2.
```

2. The **SYNOPSIS** section gives a brief overview on how to use the function, including its header file and prototype.  For example,

```
SYNOPSIS
     #include <string.h>
     int strcmp(const char *s1, const char *s2);
```

3. The **RETURN VALUE** section explains what will be returned. For example,

```
RETURN VALUES
     The strcmp() and strncmp() functions return an integer greater than,
     equal to, or less than 0, according as the string s1 is greater than,
     equal to, or less than the string s2.
```

4. The **ERRORS** section, if exists, explains what can go wrong with the function.

