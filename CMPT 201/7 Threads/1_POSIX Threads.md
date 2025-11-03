

## Threads
- a **unit of execution**
- a "*light-weight process*"
	- Processes have **separate** address spaces (child pointers cannot access parent pointers)
	- Threads in one process **share** address space. Data sharing, especially in the heap, is easy.
	- Threads are **faster to create** compared to creating processes
- Many things happening at once in **one process**, running in multiple threads
- Any process always has the **Main Thread**, from `main()`

Each thread has **its own**
- stack
- registers
- program counter (which instruction to run now)
- `errno`, error numbers are *thread specific*

| Address Space        |
| -------------------- |
| Kernel               |
| Stack of Main Thread |
| Stack of Thread 2    |
| ...                  |
| Memory Mapping       |
| Heap                 |
| BSS                  |
| Data                 |
| Text                 |

If `fork()` is called in a thread, Linux will fork **the entire process**, include all threads in that process.

The **pthread** (stands for *POSIX Threads*) library is used to manage threads. See more info in `man pthreads`.

> [!tip] Note
> When compiling code with threads, use the `pthread` flag on `clang`.
> 
> ```
> clang -pthread -o main main.c
> ```


### Creating a thread
`pthread_create()` synopsis:
```c
#include <pthread.h>
int pthread_create(pthread_t *thread, pthread_attr_t *attr, void *(*start_routine)(void *), void *arg);
```

In the function prototype:
- `thread` is where the thread ID is stored at, where `pthread_t` is the special type used for thread IDs
- `start_routine` is the function pointer that the thread will run
	- The function will have one argument as an array of arguments

```c
static void *thread_func(void *args) {
	...
	pthread_exit(0);
}

int main() {
	pthread_t t1;
	pthread_create(&t1, NULL, thread_func, NULL);
	pthread_join(t1,NULL);
	return 0;
}
```

### Exiting a running thread
`pthread_exit()` synopsis:
```c
#include <pthread.h>
void pthread_exit(void *retval);
```

This is done implicitly when `return 0;` is called in the thread function.

### Getting the thread ID
`pthread_self()` synopsis:
```c
#include <pthread.h>
pthread_t pthread_self();
```

This returns the special thread type mentioned earlier, `pthread_t`. To get the thread ID as a number, use `gettid()`.

`gettid()` synopsis:
```c
#define _GNU_SOURCE
#define <unistd.h>
pid_t gettid(void);
```

### Waiting for a thread
`pthread_join()` synopsis:
```c
#include <pthread.h>
int pthread_join(pthread_t thread, void**retval);
```

The return value of the waited thread is stored at `retval`.

