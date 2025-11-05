

## Semaphores
- While a [[1_Locks#Mutex|Mutex]] lock is **binary**, either locked or unlocked
- Semaphores are locks **with counts**
	- indicates **how many** are available
	- If availability is 0, then it is unavailable
	- If availability is >0, then it is available

> [!warning] Note
> Semaphores do **not guarantee** [[1_Locks#Mutex|mutual exclusion]] to a [[1_Locks#Critical section|critical section]]. It only counts the availability of a resource.

### Initializing a semaphore
```c
sem_t sem;
sem_init(sem_t *sem, int pshared, unsigned int value);
```

In `sem_init`:
- `sem` is the pointer to the semaphore (defined in the first line)
- `pshared` indicates the use
	- `0` for threads
	- `1` for processes
- `value` is the initial max count of how many is available

### Acquiring a semaphore count
`sem_wait` synopsis:
```c
#include <semaphore.h>
int sem_wait(sem_t *sem);
```

- If the semaphore count is 0, it **blocks** and waits until count is >0
- If the semaphore count is >0, it **decrements** the count and returns

Similar to [[1_Locks#Locking|locks]], we can use `trywait` and `timedwait` to limit the blocking.

`sem_trywait` and `sem_timedwait` synopsis:
```c
#include <semaphore.h>
int sem_trywait(sem_t *sem);
int sem_timedwait(sem_t * sem, struct timespec *abs_timeout);
```

### Counting up the semaphore
`sem_post` synopsis:
```c
#include <semaphore.h>
int sem_post(sem_t *sem);
```

- **Increases** the semaphore count and returns
- Used for:
	- releasing a resource
	- producing a new resource

