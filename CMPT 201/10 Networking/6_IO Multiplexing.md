

## Epoll
- Using Syscalls to **monitor** multiple file descriptors
- The kernel **notifies** program on socket event
- Handle **multiple clients** without the use of threads

Multiplexing process:
- Add file descriptors to a **monitored list**
- Indicate what to monitor (ready to read, write)
- Call blocking function to **wait for** an event
- When returned, check which file descriptor on the list can perform I/O
- Perform the I/O

> [!warning] Note
> Epoll, compared to using threads, adds complexity to the code, but wastes less system resources.


### Creating an epoll
`epoll_create` synopsis:
```c
#include <sys/epoll.h>
int epoll_create(int size);
```

`epoll_create` returns an epoll instance, the monitor **list** 

### Configuring an epoll
`epoll_ctl` synopsis:
```c
#include <sys/epoll.h>
int epoll_ctl(int epfd, int op, int fd, struct epoll_event *event);
```

`epoll_ctl` adds, removes, or modifies a file descriptor to the epoll instance

### Waiting for an event
`epoll_wait` synopsis:
```c
#include <sys/epoll.h>
int epoll_wait(int epfd, struct epoll_event *events, int maxevents, int timeout);
```

`epoll_wait` waits for a file descriptor to be available for I/O