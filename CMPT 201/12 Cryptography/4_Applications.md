

## Cryptographic Application

### Storing Passwords
- Passwords are stored only in [[2_Hash functions|Hash]]
- **No plain text** is stored

Whenever a password is entered to the log-in:
- The system **hashes** the input
- It **compares** the hash with the stored hash
- If they **match**, the password is correct

If an unauthorized party accesses the database, they can only get **the hash** that cannot be used to log in.

Linux stores the password hash in `/etc/shadow`

### Salting
- If many users have the same password (e.g., `password`, `1234`, `12345`), it will be **obvious** that the hashes are the same
- This is vulnerable to **Rainbow Table Attack**, where attackers **pre-compute** a table of the hash of common passwords that they can quickly search through

Example of rainbow table using `md5` hashing:

| String     | Hash                               |
| ---------- | ---------------------------------- |
| `password` | `5f4dcc3b5aa765d61d8327deb882cf99` |
| `12345`    | `827ccb0eea8a706c4c34a16891f84e7b` |
| `123456`   | `e10adc3949ba59abbe56e057f20f883e` |

> [!warning] Note
> `md5` is found to be insecure by 2005, no longer in use

Note that changing just one letter in the string (`12345` → `123456`) makes the hash **very different**.

A **salt** is a random number or string added to the end of the password
- For example, `password` → `password$#j993` where salt=`$#j993`

| Salt     | Hashed Password                    |
| -------- | ---------------------------------- |
| `$#j993` | `a2931c512206243add6021f5fdc1208b` |
- Both the **salt** and the **hashed password** are **stored** in database
- When the user logs in, the system **adds the salt** to the input, and compares the hash with the stored hash
- This protects users that have the same passwords, and against rainbow table attacks

### Verifying documents: Secure Digest
- Verify that a file is **not corrupted**
- Generates a **summary**
	- Fixed length string that characterizes an arbitrary length message
	- Typically uses the `SHA-256` hash function
- Needs a hash of the legitimate file
- Hash the file we have, and check if the hashes match
- If they do, the file is not tampered with

### Digital Signature
- Verify that a message is **unaltered** and produced **by the signer**
- Combines [[3_Asymmetric Encryption|Public key]] and [[2_Hash functions|Hashing]]
- The message does not have to be private

![[chart05.png]]

The signer:
- **hashes** the message into a digest
- encrypts **the digest** (*signing*) of the message using their private key
- sends the encrypted digest with the message

The verifier:
- decrypts the digest using the signer's public key
- **hashes** the message
- compares the hash with the decrypted digest

If they match, the message is verified.

![[chart04.png]]


### Digital Certificate
- While the receiver can [[3_Asymmetric Encryption#Verifying the sender|verify]] that the message belongs to the sender, this **assumes** that the receiver has the sender's real public key
- A third party could **disguise** as the sender and give the receiver a fake public key

A **digital certificate** is used in **HTTPS** (HTTP***Secure***)
- The certificate proves that the public key belongs to the website owner
- The OS has built-in **trusted** signing authorities, vouching services
	- Signing authorities like VeriSign or DigiCert establish **root of trust**
	- OS is shipped with the public keys of these authorities
- The browser then uses the trusted public key

![[chart07.png]]

For example, the website `*.tinagrit.com` is signed by the signing authority "Let's Encrypt" of the US
- The owner of the website gives the signing authority a public key
- The authority **signs a certificate** using its private key
- The certificate confirms that the website's public key belongs to the website

![[chart06.png|400]]

When accessing a website:
- The website sends its **digital certificate** to the browser through HTTP (*unencrypted*)
- The browser **attempts to decrypt** the certificate, using one of the trusted public keys in the OS
- If successful, then the website is signed by a trusted authority, and the website's **public key is retrieved** through the decrypted certificate
- Now that the browser has a trusted public key of a website, it may begin transmitting through HTTPS (*secure*)

![[chart09.png|500]]

This process ensures that the public key **belongs** to the website the user is accessing.
- The public key is used to exchange a **new secret key**, used to exchange information using [[1_Cryptography#Cryptographic algorithms|a symmetric encryption]] (faster than asymmetric)


> [!tip] Chain of Trust
> - To trust the website's public key, we need to trust **the signing authority**
> - To trust the signing authority, we need to trust that the **OS is not compromised**


---

## Birthday Attack

- In a class of 30 people, there is a **70%** chance that two people have the **same birthday**
- Similarly, given enough messages, there could be a **hash collision** between two messages
	- Two messages have the same hash
	- Showing that a hash function **does not achieve** [[2_Hash functions#Hash functions|Strong collision resistance]] (it is not hard to find two values with the same hash)

![[chart11.png]]

The Birthday attack works by:
- The attacker creates multiple copies of **benign contracts** that look the same as the original contract (small typo, spaces, commas)
- The attacker then finds a **benign contract** that has **the same hash** (*hash collision*) as the **original contract**
- The attacker sends the benign contract to the customer, for them to sign with their private key
- The attacker can claim that the customer signed the **malicious contract**, since it is signed by the customer's private key

