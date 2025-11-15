

## Network Socket Interface
- **Socket** is an abstraction of an endpoint
	- Application can use to **communicate** with another process
	- Local or remote
- The **Active Socket** is the client that connects to a server
- The **Passive Socket** is the server that accepts connections
- Basic Socket Syscalls
	- [[#Creating a socket|socket]]
	- [[#Binding a socket|bind]]

> [!warning] Note
> A socket is a **file** and can be listed using `ls`. Remove a socket after using.


### Creating a socket
`socket()` synopsis:
```c
#include <sys/socket.h>
int socket(int domain, int type, int protocol);
```

`socket()` returns the [[1_File Syscalls#File descriptor|File descriptor]]
- Can be used with socket specific calls, like `send()`, `recv()`, `sendto()`, `recvfrom()`

In the function prototype:
- `domain` refers to the **set of rules** that an entity needs to follow to communicate with another entity, for example:
	- `AF_UNIX`: Local communication in the same computer
	- `AF_INET`: IPv4 IP addresses
	- `AF_INET6`: IPv6 IP addresses
- `type` is either [[1_Network Stack#Transport|TCP or UDP]]
	- `SOCK_STREAM` is the [[3_TCP Type#TCP Connection|TCP]], sequenced reliable two-way connection
	- `SOCK_DGRAM` (for *datagram*) is the [[4_UDP Type#UDP Connection|UDP]], connectionless, unreliable packets
- `protocol`, keep it `0` since it is not used for the domains listed above


### Binding a socket
`bind()` synopsis:
```c
#include <sys/socket.h>
int bind(int sockfd, struct sockaddr *addr, socklen_t addrlen);
```

`bind()` binds the **socket** to an **address**
- Uses a generic `sockaddr` struct, where different protocol uses different struct
- When passing different structs into `bind()`, **type cast** the struct into `sockaddr`

```c
struct sockaddr {
	sa_family_t sa_family;
	char        sa_data[14];
}
```

For a `AF_UNIX` socket, (see more in `man unix`):
- include `#include <sys/un.h>`
- the `sockaddr` is defined as follows:

```c
struct sockaddr_un {
	sa_family_t sun_family;
	char        sun_path[108];
}
```

The `sun_path` refers to the **name of the socket** instead of the port number, and can be any string.

For example, we can do as follows to bind a local socket:
```c
struct sockaddr_un saddr;
saddr.sun_family = AF_UNIX;
snprintf(saddr.sun_path, 108, "my_socket");

bind(sfd, (struct sockaddr *)&saddr, sizeof(saddr))
```

