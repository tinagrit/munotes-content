

## First In First Out
- A **named pipe**, similar to [[2_Sockets#Binding a socket|UNIX domain sockets]]
- **Unrelated processes** (not parent/child) cannot share a pipe, but they can share FIFOs.
	- They only need to know a **pathname** of the FIFO
- FIFO is **unidirectional**, same as pipes
	- An `open()` call **blocks** until a different process can `open()`

### Creating a FIFO
`mkfifo` synopsis:
```c
#include <sys/types.h>
#include <sys/stat.h>
int mkfifo(char *pathname, mode_t mode);
```

In the function prototype:
- `pathname` is the string of pipe name
- `mode` is the same as the `mode` in [[1_File Syscalls#Opening a file|open()]]

### Example

Client
```c
int main() {
	char *toSend = "Hello world";
	
	int fd = open("my fifo", O_WRONLY);
	write(fd, toSend, strlen(toSend));
	
	close(fd);
	return 0;
}
```

Server
```c
int main() {
	mkfifo("my fifo", S_IRUSR | S_IWUSR);
	int fd = open("my fifo", O_RDONLY);
	
	while(read(fd, readbuf, sizeof(readbuf)) > 0) {
		printf("Received: %s\n", readbuf);
	}
	
	close(fd);
	return 0;
}
```

