

## Reentrant functions
A **reentrant function** refers to a function that:
- safely runs even when **called again** while it is being executed
- not only it has to be thread safe, it should also handle **asynchronous** calls from the **same thread**, e.g. signal handler

> [!warning] Note
> `printf()` is **not** a reentrant function. As mentioned in [[1_Signals#Signals|Signals]] that it is not signal-safe.
> 
> A reentrant function needs to be [[1_Locks#Thread safety|thread safe]] and [[1_Signals#Signals|signal safe]].

Mutex [[1_Locks#Locking|locking]] causes a function to be non-reentrant. An example:
- The `main()` and a signal handler access shared resources, so a lock is introduced for Critical Sections
- The `main()` gets run and **is now holding the lock**
- A signal call interrupts the execution and the signal handler gets run
- A call to lock from the signal handler sees that a lock is being held, and waits for the lock
- Since both `main()` and the handler are on the **same thread**, `main()` never gets the chance to release the lock, and the handler waits for that lock forever


### Function safety examples

This swap function:
```c
int tmp = 0;
int swap(int *a, int *b) {
	tmp = *a;
	*a = *b;
	*b = tmp;
}
```
- is **not thread safe**, and therefore **not reentrant**
- `tmp` is a global variable, so multiple threads calling this function at the same time will break


This swap function:
```c
int tmp = 0;
pthread_mutex_t mutex = PTHREAD_MUTEX_INITIALIZER;
int swap(int *a, int *b) {
	pthread_mutex_lock(&mutex);
	tmp = *a;
	*a = *b;
	*b = tmp;
	pthread_mutex_unlock(&mutex);
}
```
- is **thread safe**
- Due to the use of Mutex locks, this function is **not signal safe**, and therefore **not reentrant**


This swap function:
```c
int swap(int *a, int *b) {
	int tmp = 0;
	
	tmp = *a;
	*a = *b;
	*b = tmp;
}
```
- is **thread safe** due to no shared data
- No saved or shared data leads to no contention, and therefore **is reentrant**


### Making function reentrant

If a function is not reentrant, there is contention on a shared data. Functions that work with **buffers** can:
- allocate its own **local variable** buffer on the stack
- **dynamically** allocate and free buffer in the heap
- have the **calling code allocate** and passing in pointers
	- powerful solution since it gives the caller freedom to choose what happens
	- space returned to the caller or maintained across functions is allocated **by the caller**

C Standard Library functions that end with `_r` refers to it being **reentrant**, such as `strtok_r` requiring callers to pass in the buffer.


---
## Deadlock
- is when a set of threads each:
	- **hold** a resource (lock)
	- **wait** to acquire a resource held by another (trying to lock another thread's locked resource)
- For example:
	- Thread 1 locks resource A
	- Thread 2 locks resource B
	- Thread 1 waits for resource B to be unlocked, whilst still locking A
	- Thread 2 waits for resource A to be unlocked, whilst still locking B
- **Nothing gets done** because threads are waiting for each other

> [!warning] Note
> A program with deadlock is a [[2_Data Race#Deterministic programs|non-deterministic]] program.

### Conditions for a deadlock
Necessary for deadlock, but don't guarantee it. If all 4 conditions hold, a deadlock **is possible**.

1. **Hold and wait**
	- Threads already holding resources
	- Also waiting for additional resources
2. **Circular wait**
	- T0 is waiting for T1
	- T1 is waiting for T2
	- T2 is waiting for T3
	- ...
	- Tn is waiting for T0
3. **Mutual exclusion**
	- Threads hold resources exclusively
	- We can't have a deadlock if there isn't Mutex
4. **No preemption**
	- Resources released only voluntarily by the holder
	- Cannot force someone to release resources

### Preventing deadlocks
1. Grab **all locks** atomically
	- Grab all locks or no locks at all
	- Breaking hold and wait
	- Lock the lock codes **all at once**
	- Can [[1_Locks#Locking|use]] `trylock` and try again later
2. Grab locks in the **same order**
	- Acquire locks in the same order **for all threads**
	- Breaking circular waits
	- Can never be waiting for another thread waiting for the current thread


---
## Livelock
- is when a set of threads
	- each **actively execute** instructions
	- but not making progress
- similar to a hold and wait condition of [[#Deadlock|Deadlocks]]

For example, in pseudo code:

Thread 1:
```python
while true:
	acquire(resource1)
	if resource2 is free:
		acquire(resource2)
		...
	else:
		release(resource1)
```

Thread 2
```python
while true:
	acquire(resource2)
	if resource1 is free:
		acquire(resource1)
		...
	else:
		release(resource2)
```

While these thread codes look fine, each thread, line-by-line can be run **at the same time**.
- This can run forever, or until the line-by-line synchronization breaks up
- This is a [[2_Data Race#Deterministic programs|non-deterministic]] behaviour

