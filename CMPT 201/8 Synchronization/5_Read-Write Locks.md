

## Read-Write Locks
- Synchronization primitive that allows **either**:
	- unlimited readers
	- one writer
- Nobody can access the data while someone is writing it

### Defining a read-write lock
```c
pthread_rwlock_t rwlock = PTHREAD_RWLOCK_INITIALIZER;
```

### Acquire a reading lock
`pthread_rwlock_rdlock` and `pthread_rwlock_tryrdlock` synopsis:
```c
#include <pthread.h>
int pthread_rwlock_rdlock(pthread_rwlock_t *rwlock);
int pthread_rwlock_tryrdlock(pthread_rwlock_t *rwlock);
```

- Returns immediately if **no thread** has acquired a **writing lock**
- Waits on the writing thread if one has locks writing

### Acquire a writing lock
`pthread_rwlock_wrlock` synopsis:
```c
#include <pthread.h>
int pthread_rwlock_wrlock(pthread_rwlock_t *rwlock);
```

- Allows only one thread to lock writing

