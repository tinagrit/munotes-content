

## Using sockets on a network
- Instead of a socket name ,use **IP Addresses**
	- IPv4: `AF_INET` uses 4 bytes
	- IPv6: `AF_INET` uses 16 bytes, in use since we are running out of IPv4
- Instead of using `sockaddr_un` for local transmission, we will use `sockaddr_in` where `in` stands for **internet**. (see more in `man inet`):
	- include `#include <netinet/in.h>`
	- the `sockaddr` is defined as follows:

```c
struct in_addr {
	in_addr_t s_addr;
}

struct sockaddr_in {
	sa_family_t    sin_family;
	in_port_t      sin_port;
	struct in_addr sin_addr;
	unsigned char  __pad[x];
}
```

Computer represents IP addresses as **4 byte binary**. Can be converted using:
- `inet_pton()` Presentation to Network (readable to binary)
- `inet_ntop()` Network to Presentation (binary to readable)

For example, to store the IP address `127.0.0.1` to the struct called `saddr`:
```c
inet.pton(AF_INET, "127.0.0.1", &saddr.sin_addr);
```

To create a buffer constant for presentation IP addresses, use:
- `#include <netinet/in.h>`
- `INET_ADDRSTRLEN` for IPv4
- `INET6_ADDRSTRLEN` for IPv6


> [!warning] Note
> **Sniffing** refers to a socket reading packets that it shouldn't.


### Loopback address
- Used for **local communication**, goes back to the host
- `127.0.0.1`
- Nothing goes on the network

```c
s_addr = INADDR_LOOPBACK;
```


### Wildcard address
- Used to **talk to anybody**, without picking address
- `0.0.0.0`
- If we [[2_Sockets#Binding a socket|bind a socket]] to `INADDR_ANY`, it listens to any address

```c
s_addr = INADDR_ANY;
```


### Binding a network socket
See [[2_Sockets#Binding a socket|Binding a socket]]

`bind()` now needs an **IP address** and a **port number**
- The port number identifies a specific socket
- SSH uses port 22
- HTTP uses port 80

If we don't `bind()` to one specific port, TCP or UDP will pick a **Ephemeral port**, an unused random port.
- This can be useful with **active sockets** when they don't care what port


### Hostname
- The **computer name**, in use instead of the IP address

Can be found using:
- `getaddrinfo()` converts Computer Name to possible IPs (struct)
- `getnameinfo()` converts IP to Computer Name


---
## Byte Order
- Different architectures use **different** byte order

Consider the number `12345` represented in hexademical `0x3039`
- **Little Endian** stores the LSB (*least significant byte*) first, will store the number as `39 30`
	- Most systems use Little Endian internally
- **Big Endian** stores the MSB (*most significant byte*) first, will store the number as `30 39`

>[!tip] Note
> The **Big Endian** is used by **Network Byte Order**, establishing the same byte order for communication.

Can be converted using:
- `#include <arpa/inet.h>`
- `htonl()` Host to Network (long, 16 bytes)
- `htons()` Host to Network (short, 4 bytes)
- `ntohl()` Network to Host (long, 16 bytes)
- `ntohs()` Network to Host (short, 4 bytes)


---
## TCP Example

Passive Socket in `AF_INET`
```c
int main() {
	// socket
	int sfd = socket(AF_INET, SOCK_STREAM, 0);
	if (sfd == -1) {
		// Socket failed
	}
	
	// bind
	struct sockaddr_in saddr;
	saddr.sin_family = AF_INET;
	saddr.sin_port = htons(8000);
	saddr.sin_addr.s_addr = htonl(INADDR_ANY);
	
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

Active socket in `AF_INET`
```c
int main() {
	// socket
	int sfd = socket(AF_INET, SOCK_STREAM, 0);
	if (sfd == -1) {
		// Socket failed
	}
	
	// connect
	struct sockaddr_in saddr;
	saddr.sin_family = AF_INET;
	saddr.sin_port = htons(8000);
	inet.pton(AF_INET, "127.0.0.1", &saddr.sin_addr);
	
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
