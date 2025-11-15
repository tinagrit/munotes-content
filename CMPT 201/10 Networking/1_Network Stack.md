

## Network Stack
- **Networking** allows programs **communicating** with each other
	- Can be across network, or the same computer
- **Stacks** organize the networking responsibility into **layers**
	- Each layer service the layer **above** it

| Network Stack                                       |
| --------------------------------------------------- |
| [[#Application\|Application]]                       |
| [[#Transport\|Transport]]                           |
| [[#Internet Protocol (IP)\|Internet Protocol (IP)]] |
| [[#Link (MAC)\|Link (MAC)]]                         |
| [[#Physical\|Physical]]                             |

### Physical
- **hardware** control
- generating and receiving data
- focuses on **voltage** and **signals**
- For example, Wi-Fi, antenna, radio, Ethernet

### Link (MAC)
- does **local** network addressing and routing
	- same Wi-Fi, or physical Ethernet through a switch
- **LAN** refers to Local Area Network
- Each device talks to each other using a **MAC Address**
	- refers to *Medium Access Control*
	- looks like `a0:78:17:8c:9b:ce`
	- is **unique** to **every device** in the world
	- includes the **vendor** and a unique ID, like a serial number

### Internet Protocol (IP)
- does **inter-networking** addressing and routing
- A common **organization** between networks
- uses the **IP Address** for addressing
	- looks like `192.75.244.48`
	- Some IPs, such as `10.x.x.x`, `192.168.x.x` are **non-routable** on the Internet and preserved for local use

### Transport
- does packet **tracking** and **retransmission**
- 3 common issues with sending and receiving packages
	1. **lost** packages
	2. **out of order** packages
	3. **duplicated** packages
- The **raw packages** being sent and received is called the **UDP** (*User Datagram Protocol*)
- If an application requires a **reliable** ordered stream
	- It can use the **TCP** (*Transmission Control Protocol*)
	- No loss, no out of order, no duplication
	- TCP uses the UDP packets
- uses the **Port Number**
	- identifies **where** in the computer or which application to send data to
	- For example, port `80` is generally for HTTP, and port `443` is generally for HTTPS

### Application
- what the application **is doing** with networking
- can feature well-known protocol like HTTP and FTP