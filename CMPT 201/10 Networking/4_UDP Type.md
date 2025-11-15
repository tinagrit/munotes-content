

## UDP Sockets
- used to send connectionless, unreliable packets
- **no established connection** is required

| Passive Socket<br>(Server) |     | Active Socket<br>(Client) |
| -------------------------- | --- | ------------------------- |
| `socket()`<br>`bind()`<br> |     |                           |
|                            |     | `socket()`                |
| `recvfrom()`               | ←   | `sendto()`<br>            |
| `sendto()`                 | →   | `recvfrom()`              |
| `close()`                  |     | `close()`                 |
- `recvfrom()` is a **blocking** call to wait for a message arrival
- Handle new messages **one at a time**, instead of having each connection for each active socket


### Receiving data
`recvfrom()` synopsis:
```c
#include <sys/socket.h>
ssize_t recvfrom(int sockfd, void buf[len], size_t len, int flags, struct sockaddr *src_addr, socklen_t *addrlen);
```

In the function prototype:
- `sockfd` refers to the file descriptor created by `socket()`
- `buf` and `len` are the **buffers of data** to be received
- `flags` refer to options in receiving, or leave `0` for no flags
- `src_addr` and `addrlen` are the **source** socket defined in a `sockaddr` struct, or leave `NULL` for accepting from any socket

`recvfrom()` returns the number of **received bytes**


### Sending data
`sendto()` synopsis:
```c
#include <sys/socket.h>
ssize_t sendto(int sockfd, void buf[len], size_t len, int flags, struct sockaddr *dest_addr, socklen_t addrlen);
```

`sendto()` transmits a message to another socket
In the function prototype:
- `sockfd` refers to the file descriptor created by `socket()`
- `buf` and `len` are the **data** to be sent
- `flags` refer to options in sending, or leave `0` for no flags
- `dest_addr` and `addrlen` are the **destination** socket defined in a `sockaddr` struct

`sendto()` returns the number of **written bytes**


### Example

Passive Socket in `AF_UNIX`
```c
int main() {
	// socket
	int sfd = socket(AF_UNIX, SOCK_DGRAM, 0);
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
	
	// Keep receiving
	while (true) {
		// recvfrom
		const int BUFFER_SIZE = 1024;
		char buffer[BUFFER_SIZE];
		int bytes_read; 
		
		if (recvfrom(sfd, buffer, BUFFER_SIZE, 0, NULL, NULL) == -1) {
			// Recvfrom failed
		}
		
		printf("%s", buffer);
	}
	
	// close
	close(sfd);
	return 0;
}
```

Active socket in `AF_UNIX`
```c
int main() {
	// socket
	int sfd = socket(AF_UNIX, SOCK_DGRAM, 0);
	if (sfd == -1) {
		// Socket failed
	}
	
	// sendto
	struct sockaddr_un saddr;
	saddr.sun_family = AF_UNIX;
	snprintf(saddr.sun_path, 108, "my_socket");
	
	char message[14] = "Hello World!\n";
	int bytes_written = sendto(sfd, message, strlen(message), 0, (struct sockaddr *)&saddr, sizeof(saddr));
	if (bytes_written == -1) {
		// Sendto failed
	}
	
	// close
	close(sfd);
	return 0;
}
```

