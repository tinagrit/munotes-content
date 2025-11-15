

## TCP Connection
- used to send sequenced, reliable, two-way connection data
- creates an **established connection**

| Passive Socket<br>(Server)                         |       | Active Socket<br>(Client) |
| -------------------------------------------------- | ----- | ------------------------- |
| `socket()`<br>`bind()`<br>`listen()`<br>`accept()` |       |                           |
|                                                    | <br>← | `socket()`<br>`connect()` |
| `read()`                                           | ←     | `write()`                 |
| `write()`                                          | →     | `read()`                  |
| `close()`                                          |       | `close()`                 |
- `accept()` is a **blocking** call by the passive socket, waits for a connection attempt
- Each `read()` and `write()` includes lower level protocol, like an **acknowledgement**


### Marking socket as passive
`listen()` synopsis:
```c
#include <sys/socket.h>
int listen(int sockfd, int backlog);
```

A socket is by default active, calling `listen()` will make the socket **passive**.

In the function prototype:
- `sockfd` refers to the file descriptor created by `socket()`
- `backlog` is the maximum length of **pending connections**
	- If the queue is full, any new connections will be refused


### Accepting a connection
`accept()` synopsis:
```c
#include <sys/socket.h>
int accept(int sockfd, struct sockaddr *addr, socklen_t *addrlen);
```

`accept()` accepts a new connection, and returns **a new socket** for the new connection
- The old socket is only used to accept connections
- Talk to the new connection on a brand new port

Standard practice to **call `accept()` in a loop**
- `accept()` **blocks** until there is a connection attempt

In the function prototype:
- `sockfd` refers to the file descriptor created by `socket()`
- `addr` and `addrlen` is the pointers to a `sockaddr` structure, filled with the address of a **peer socket**, or `NULL` if nothing is sent back 


### Connecting to a passive socket
`connect()` synopsis:
```c
#include <sys/socket.h>
int connect(int sockfd, struct sockaddr *addr, socklen_t addrlen);
```

`connect()` requires an established connection first.
- Called by the **active socket** to the passive socket


### Example

Passive Socket in `AF_UNIX`
```c
int main() {
	// socket
	int sfd = socket(AF_UNIX, SOCK_STREAM, 0);
	if (sfd == -1) {
		// Socket failed
	}
	
	// Remove existing socket (if any)
	if (remove("my_socket") == -1 && errno != ENOENT) {
		// Remove failed
	}
	
	// bind
	struct sockaddr_un saddr;
	saddr.sun_family = AF_UNIX;
	snprintf(saddr.sun_path, 108, "my_socket");
	
	if (bind(sfd, (struct sockaddr *)&saddr, sizeof(saddr)) == -1) {
		// Bind failed
	}
	
	// listen
	if (listen(sfd, 10) == -1) {
		// Listen failed
	}
	
	// Keep accepting connections
	while (true) {
		// accept
		int connectedfd = accept(sfd, NULL, NULL);
		if (connectedfd == -1) {
			// Accept failed
		}
		
		// read
		const int BUFFER_SIZE = 1024;
		char buffer[BUFFER_SIZE];
		int bytes_read; 
		
		// Keep reading from the same client
		while ((bytes_read = read(connectedfd, buffer, BUFFER_SIZE)) > 0) {
			// Writing what is read to the terminal
			printf("%s", buffer);
		}
		
		if (bytes_read == -1) {
			// Read failed
		}	
	}
	
	// close
	close(connectedfd);
	close(sfd);
	return 0;
}
```

Active socket in `AF_UNIX`
```c
int main() {
	// socket
	int sfd = socket(AF_UNIX, SOCK_STREAM, 0);
	if (sfd == -1) {
		// Socket failed
	}
	
	// connect
	struct sockaddr_un saddr;
	saddr.sun_family = AF_UNIX;
	snprintf(saddr.sun_path, 108, "my_socket");
	
	if (connect(sfd, (struct sockaddr *)&saddr, sizeof(saddr)) == -1) {
		// Connect failed
	}
	
	// write
	char message[14] = "Hello World!\n";
	int bytes_written = write(sfd, message, strlen(message));
	if (bytes_written == -1) {
		// Write failed
	}
	
	// close
	close(sfd);
	return 0;
}
```

