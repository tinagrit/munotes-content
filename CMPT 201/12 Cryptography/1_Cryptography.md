

## Cryptography

### The CIA Security Model
- **C**onfidentiality - Information only **disclosed** to those authorized
- **I**ntegrity - Information only **modified** in allowed ways, by authorized parties
- **A**vailability - Information **not prevented** from those authorized for access

### Cryptographic Process
Cryptographers invented secret codes to hide messages
- Plain text gets **encrypted** into Cipher text
- Cipher text gets **decrypted** into Plain text

Challenges include:
- Hiding a message from **everyone but** the intended recipient
- Making sure the message is **authentic**

### Traditional Cryptography: Caesar Cipher
- **Shift each letter** by a certain number down the alphabet
- For example, +1 shifts 'A' to 'B'
	- "Hello World" becomes "Ifmmp Xpsme"
- Not effective, since only 26 tries (# of alphabets) needed to crack
- When the algorithm is **compromised**, the code is useless

### Modern Cryptography
- Algorithms are **public** but **keys** are secret
- More effective, since it no longer requires the algorithm to be private
	- If the **secret key** becomes public, then just **replace it** with a new one
- A cryptographic algorithm:
	- Given a key, **easily decrypt** a message
	- Without a key, **hard to invert** a message
- The **key length** defines the security strength, harder to brute force

A cryptographic algorithm **will be compromised** at some point.
- The **Window of Validity** is the minimum time to compromise one
- Must only use an algorithm that has yet to be compromised
- The window may be **shorter than** the lifespan of the system
- A system should be designed such that the crypto function can be **easily replaced**

Currently, `SHA-256` is widely used, and has yet to be compromised.


## Cryptographic algorithms

- Categorized based on the number of keys
	- **0 keys**: [[2_Hash functions|Cryptographic hash functions]]
	- **1 key**: Secret-key functions (Symmetric encryption)
		- A **private key** is required to encrypt or decrypt a message
		- Requires a way to privately share the key
		- An example encryption is `AES`
	- **2 keys**: [[3_Asymmetric Encryption|Public-key functions (Asymmetric encryption)]]

