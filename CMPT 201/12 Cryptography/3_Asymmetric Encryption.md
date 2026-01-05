

## Asymmetric Encryption

When data is encrypted with one key, **only the other key** can decrypt it.
- The public key can **decrypt** only Plain text encrypted with a private key.
- The private key can **decrypt** only Plain text encrypted with a public key.

![[chart01.png]]

Ownership
- The public key can be known by **anybody**
- The private key can only be known to the **owner of the key**

> [!tip] The two keys are like "inverses" of each other
> - Applying the same algorithm using each key **gets back** the original message
> - The two keys are **generated together**, very hard to reverse computation
> 	- For example, multiplying two large prime numbers is easy, but finding two prime numbers that multiply to a large number is difficult


### Verifying the sender
The two-way encryption can be combined to ensure that both
- only the **recipient** can read
- the recipient **knows** that the sender is the one sending 

This works by two parties having each other's public key

![[chart02.png]]

If `A` wants to send `B` a message,
- `A` encrypts the message using `B`'s public key
- `A` encrypts the result of the above using `A`'s private key

If `B` wants to read the message,
- `B` decrypts the cipher using `A`'s public key. Since only `A`'s private key can create a message decryptable by `A`'s public key, `B` knows that `A` is definitely the sender of the message
- `B` decrypts the result of the above using `B`'s private key

This way, only `B` can read the message, and it is verified that `A` is the sender

![[chart03.png]]

