

## Signals
- a way for processes to **communicate**, e.g. parent and child
- **Notifications** with specific meanings
- Programs and the kernel can:
	- **send signals** to itself and other programs
	- have a **signal handler** that will be called when it receives a signal

When using signals, we must use **signal safe** functions to not mess with the signal configuration.
- The list of signal safe functions can be found in `man signal-safety`
- For example, `printf()` is **not signal safe**
- To print to the terminal, we use: 

```c
write(STDOUT_FILENO, "Hello World\n", strlen("Hello World\n"));
```


### Sigaction
- After we write a signal handler, we have to **register the handler** with Linux so that it can get triggered
- The handler will be passed in as a **function pointer**

`sigaction()` synopsis:
```c
#include <signal.h>
int sigaction(int signum, struct sigaction *act, struct sigaction *oldact);
```

In the function prototype:
- `signum` refers to the signal that we want to handle, such as:
	- `SIGSEGV` for segmentation faults
	- `SIGINT` for CTRL+C
	- `SIGKILL` for `kill` call from the terminal
- `act` is a `struct` configuring the handler
- `oldact` gives back the old signal handler

`struct sigaction` definition:
```c
struct sigaction {
	void (*sa_handler)(int);
	void (*sa_sigaction)(int, siginfo_t *, void *);
	sigset_t sa_mask;
	int sa_flags;
	void (*sa_restorer)(void);
};
```

- We will mostly only use `sa_handler` to store the function pointer to the **handler**. 
- `sa_flags` can be set to `0` for no flags
- Initialize `sa_mask` to default by `sigemptyset(&act.sa_mask);`

For example, consider:
```c
void handle_signal(int signum) {
	write(STDOUT_FILENO, "CTRL+C Pressed!", strlen("CTRL+C Pressed!"));
}

int main() {
	struct sigaction act;
	act.sa_handler = handle_signal;
	act.sa_flags = 0;
	sigemptyset(&act.sa_mask);
	
	sigaction(SIGINT, &act, NULL);
	
	while (1) {
		sleep(1);
	}
}
```

This `main()` function will keep sleeping **until the user has pressed** CTRL+C , and the program will say `"CTRL+C Pressed"`.
- CTRL+C will no longer exit the program.  We need to use a different terminal to `kill` or terminate via `btop`.


### Sending a signal
- A program can use `kill()` to send a signal to a process using its **PID**
- For example, a child can send a `SIGINT` to its parent

`kill()` synopsis:
```c
#include <signal.h>
int kill(pid_t pid, int sig);
```

For example, consider:
```c
pid_t pid = fork();
if (pid == 0) {
	kill(getppid(), SIGINT);
}
```

This will send a `SIGINT` signal to the parent. If the parent doesn't have a handler for `SIGINT`, the child will effectively terminate the parent.

