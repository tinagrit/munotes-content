

## Zombie processes
- When a child process terminates, the OS **retains some information** about the exit status, taking up some memory, which `wait()` cleans up
- However, if we run a child process alongside the parent and **never call** `wait()`, the exit status is stored **forever** without being used
- This is where the `WNOHANG` option on `wait()` should be used. We can keep calling `waitpid()` **without blocking** the parent, but will clean up the child once it finshes.

For example, consider:
```c
while(1) {
	pid_t childCheck = waitpid(-1, NULL, WNOHANG);
	// do other stuff
}
```

Assuming the parent has forked a child before this,
- The parent can **keep doing other stuff** in the while loop
- The `waitpid()` will automatically clean up the child **without blocking** other code


## Orphan processes
- When the child process is still running but the **parent process has terminated**
- The child process becomes an **orphan process**
- In Linux, orphan processes become children of `init`, where `init` waits for all children

