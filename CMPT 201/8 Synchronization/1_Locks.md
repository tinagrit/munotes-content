

## Synchronization
- When having multiple threads, execution needs to be **synchronized** and coordinated
- Avoids **race cases**, as they can be very difficult to debug
	- Race cases are rare
	- Debugging requires attention to multiple threads at the same time


---
## Mutex
- One operation, like `counter++` mentioned in [[2_Data Race|Data Race]], can be a **number of operations** within it. 
- MUTEX, stands for **Mutual Exclusion** prevents the mix up of sub operations
- **Locks** can stop other threads from working on a specific resource
	- guarantees that only **one single thread** can hold a lock

[[2_Data Race#Race case|Recall]]: Since many instructions are run by calling `counter++`, the `++` operator and most functions are **not atomic**.
- Atomicity refers to operations running as **one single operation**
- Atomic operations are **all or nothing**, either everything runs, or nothing runs at all. 
- Mutex **makes** a part of code atomic

> [!warning] Note
> Locks can cause the program to be [[2_Data Race#Deterministic programs|non-deterministic]]. Whichever thread grabs the lock first, **gets to run the code first**.
> 
> It is **not guaranteed** that one specific part will grab the lock first every time. We cannot control which thread runs first.

### Thread safety
A **thread safe function** refers to a function that can be run in parallel on different threads safely, by either:
- **not accessing** shared resources at all
- provides **proper protection** for Critical Sections for shared resources

By using Mutex locks, we can make functions thread safe.

### Defining a lock
This initializes a lock to the initial open state
```c
pthread_mutex_t myLock = PTHREAD_MUTEX_INITIALIZER;
```

### Locking
`pthread_mutex_lock` synopsis:
```c
#include <pthread.h>
int pthread_mutex_lock(pthread_mutex_t *mutex);
```

A call to `pthread_mutex_lock` will lock the mutex and return, **unless the lock is occupied**.
- A lock call **is blocking**. If two threads call to lock at the same time, one thread has to wait for the current lock to be unlocked.

If we don't want to wait, we can use a non-blocking `pthread_mutex_trylock`.
`pthread_mutex_trylock` synopsis:
```c
#include <pthread.h>
int pthread_mutex_lock(pthread_mutex_t *mutex);
```
This will "try" to engage the lock. If it fails, i.e., other part of the code has it locked, it will return immediately.

We can also wait for a set amount of time before failing. 
`pthread_mutex_timedlock` synopsis:
```c
#include <pthread.h>
#include <time.h>
int pthread_mutex_timedlock(pthread_mutex_t *mutex, struct timespec *abstime);
```

### Unlocking
`pthread_mutex_unlock` synopsis:
```c
#include <pthread.h>
int pthread_mutex_unlock(pthread_mutex_t *mutex);
```


---
## Locking example

This multi-thread code suffers a data race.
```c
int count = 0;

static void *thread_func(void* arg) {
	for (int i = 0; i < 999999; i++) {
		count++;
	}
	pthread_exit(0);
}

int main() {
	pthread_t t1;
	pthread_t t2;
	
	pthread_create(&t1, NULL, thread_func, NULL);
	pthread_create(&t2, NULL, thread_func, NULL);
	
	pthread_join(t1, NULL);
	pthread_join(t2, NULL);
	
	return 0;
}
``` 

This is due to:
- both threads **sharing** `count`
- `count++` is **not** an atomic operation

This can be fixed by **locking** the `++` operation, so that each thread waits for the other `++` to complete first.

```c
int count = 0;
pthread_mutex_t mutex = PTHREAD_MUTEX_INITIALIZER;

static void *thread_func(void* arg) {
	for (int i = 0; i < 999999; i++) {
		pthread_mutex_lock(&mutex);
		count++;
		pthread_mutex_unlock(&mutex);
	}
	pthread_exit(0);
}

...
```

### Critical section

The lock above could have been expanded to the **whole loop**, i.e:
```c
pthread_mutex_lock(&mutex);
for (...) 
pthread_mutex_unlock(&mutex);
```
- However, there is a performance difference. 
- It is **faster** to lock the **fewest** amount of operations called the **critical section** (CS)
	- parts that cannot be run in parallel by >1 thread
	- accesses a shared variable
- If we lock the entire loop, we will allow either `t1` or `t2`, whichever one grabs the lock first, to **fully complete the increment**, then hand it over to another
- Locking only the `++` operation will still allow two threads working together, just not interfering with one another

An ideal solution for a CS solution requires:
1. **Mutual exclusion** - only one thread is allowed to run in the CS
2. **Progress** - thread should eventually complete
3. **Bounded waiting** - an upper bound should exist for a thread waiting to access the CS


