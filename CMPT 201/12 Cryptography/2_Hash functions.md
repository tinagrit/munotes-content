

## Hash functions

The hash function $h()$ takes a message $m$ of arbitrary length, and produces a smaller number $h(m)$
- For example, if $h(m)=(m^{2}) \text{ }\%\text{ }4321$
- If $m=$ `AAAA`, the hex of $m$ is  `0x41414141`, then $h(m)=2242$
- Changing a single bit from the hex of $m$ **will change the hash**

Hash functions are:
- **easy** to compute
- **one way** functions
	- Given $h(m)$, it should be difficult to reverse and find $m$
- **weak collision** resistance
	- Given $m$, it should be difficult to find an $m'$ where $h(m')=h(m)$
	- For example, if $h(m)=m\text{ }\%\text{ }100$,  then $30$ and $130$ produce the same hash, and therefore $h$ is a **bad** hash function
- **strong collision** resistance
	- Without $m$, it should be difficult to find two values $a$, $b$ where $h(a)=h(b)$


> [!tip] Note
> Hash collisions are inevitable, since the size of the hash is smaller than the data size. There is no one-to-one mapping.

Hashes are used to **verify** that the information is not tampered with.
- Checking passwords, they don't have to be stored in database, only the hash
- Checking software integrity