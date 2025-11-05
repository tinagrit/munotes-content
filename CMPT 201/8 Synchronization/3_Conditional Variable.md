

## Repeated Checks
- An **inefficiency** of a program
- One thread keeps checking a status of a resource created by **another** thread

### Example
A **Producer-Consumer** pattern is common in programming
- **Producers** are threads that create data
- **Consumers** are threads that use data

The **store data** refers to the shared data that has been produced but not yet consumed. This **needs protection**.

Consider the following code where the main thread is the **consumer** and the created thread is the **producer**
```c
pthread_mutex_t lock = PTHREAD_MUTEX_INITIALIZER;
int resource = 0;

void *producer(void *arg) {
	while(1) {
		pthread_mutex_lock(&lock);
		resource++;
		pthread_mutex_unlock(&lock);
		
		sleep(1);
	}
}

int main() {
	pthread_t thread;
	pthread_create(&thread, NULL, producer, NULL);
	
	while(1) {
		pthread_mutex_lock(&lock);
		// consume all
		while(resource > 0) {
			resource--;
		}
		pthread_mutex_unlock(&lock);
	}
}
```

- There is **no [[2_Data Race#Race case|data race]]** because locks are placed appropriately
	- Atomic operation for producing 1 (`resource++`)
	- Atomic operation for consuming all (`while(resource>0)`)
- There is **no [[2_Contention#Deadlock|deadlock]] or [[2_Contention#Livelock|livelock]]** because there only exists 1 lock

However, there is a **major inefficiency** in this code.
- The main thread, inside of `while(1)`, repeated grabs the lock and checks if the resource exists.
- If the producer produces the resource more slowly, the main thread will **waste a lot of CPU power** trying to keep checking when the resource becomes available

This can be solved using a **Conditional Variable**


---
## Conditional Variable
- signals a **change in state** 
- works by coordinating threads
	- One thread **sends notification** to the conditional variable
	- Another thread **waits** to **receive notification** from the conditional variable
	- While waiting, the thread is asleep, i.e. no CPU usage
- integrates closely with [[1_Locks#Mutex|Mutex]]
	- **only** holds a lock while processing data
	- other threads can work while waiting

### Defining the conditional variable
```c
pthread_cond_t cond = PTHREAD_COND_INITIALIZER;
```

### Waiting on a conditional variable
`pthread_cond_wait` synopsis:
```c
#include <pthread.h>
int pthread_cond_wait(pthread_cond_t *cond, pthread_mutex_t *mutex);
```

This function has to be called **inside a lock**, i.e. a lock has to be grabbed. This will:
- release the lock
- goes asleep and wait for `cond`

The release and wait are done **atomically** to ensure that no new data (state change) occurred in between.

While it is asleep, the lock is **not held** so that other threads can still work on other things.
Once `cond` becomes available, the lock **is grabbed** and execution continues.

### Waking up a thread
`pthread_cond_signal` synopsis:
```c
#include <pthread.h>
int pthread_cond_signal(pthread_cond_t *cond);
```

More suitable if sleeping threads work **on the same thing**
- If any of the sleeping thread is sufficient to do the job
- Imagine ringing a bell at a front desk; only one attendant is expected to respond

Will only wake up **one thread**
- If there is **1 thread** sleeping, that thread wakes up and grabs the lock
- If there are **2+ threads** sleeping, only one thread wakes up, but **no control** over which one
- If no threads are sleeping, the signal is lost

### Waking up all threads
`pthread_cond_broadcast` synopsis:
```c
#include <pthread.h>
int pthread_cond_broadcast(pthread_cond_t *cond);
```

More suitable if sleeping threads work **on different things**
- If all sleeping threads are required to do the job
- Imagine many people waiting to prepare ingredients after they are taken out of the fridge; everyone is expected to attend

Will wake up **everyone**
- This wakes up **all sleeping threads**
- Everyone wakes up and **compete** to grab the lock

### Example
Consider the optimized producer-consumer code
```c
pthread_mutex_t lock = PTHREAD_MUTEX_INITIALIZER;
pthread_cond_t cond = PTHREAD_COND_INITIALIZER;
int resource = 0;

void *producer(void *arg) {
	while(1) {
		pthread_mutex_lock(&lock);
		resource++;
		pthread_mutex_unlock(&lock);
		
		pthread_cond_signal(&cond);
		
		sleep(1);
	}
}

int main() {
	pthread_t thread;
	pthread_create(&thread, NULL, producer, NULL);
	
	while(1) {
		pthread_mutex_lock(&lock);
		
		while(resource == 0) {
			pthread_cond_wait(&cond,&lock);
		}
		
		while(resource > 0) {
			resource--;
		}
		pthread_mutex_unlock(&lock);
	}
}
```

Now, whenever the main thread grabs the lock, if there is nothing to consume (`resource==0`), it will **release the lock** and wait until the producer sends a signal.

The `pthread_cond_wait` is in a `while` loop because it is **not guaranteed** that a data is available after the signal.
- This thread is waiting on the `cond`, but other threads might be waiting on the same thing
- Before waking up, other threads **may have consumed** the resource
- Checking using `if` is not sufficient


