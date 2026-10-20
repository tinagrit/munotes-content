Lectures 6-7

## RSA cryptosystem
The *Rivest-Shamir-Adleman* (**RSA**) cryptosystem is **very secure** since it takes advantage of the fact that:
- Some problems are easy for computers to solve (such as [[4_Modular Arithmetic#Exponentiation|exponentiation]], [[5_Euclids Algorithm#Greatest Common Divisor|GCD]])
- Others are extremely difficult (factoring large numbers).

The **easy** math operations to **encrypt and decrypt** messages, but breaking the encryption would require solving an extremely difficult problem.

For example, if $A$ wants to privately talk to $B$, $A$ can **encrypt** the message $e(\cdot)$, and $B$ can **decrypt** the message $d(\cdot)$, such that:
$$
d(e(x))=x
$$
If $C$ wants to read the encrypted message, without $d(\cdot)$, $C$ cannot do anything with the information.

In RSA, $e(\cdot)$ is **public**. $C$ knowing $e(x)$ still tells them little to nothing about what $x$ might be. 

This allows $A$ and $B$ to send messages to each other without having met before. $B$ generates $d(\cdot)$ and $e(\cdot)$ as inverses of each other. $B$ keeps $d(\cdot)$ a secret (**secret key**) and publishes $e(\cdot)$ to the public (**public key**).

> [!tip] RSA is secure
> By only knowing $e(\cdot)$ (the public key), it is extremely difficult to deduce $d(\cdot)$, although they are inverses of each other. The attacker must factor very large numbers, requiring more computational power than the world’s most powerful computers combined.

In this diagram, $A$ knows $B$'s public key. When a message is locked by $B$'s public key, it can **only** be unlocked by $B$'s private key.

![[chart02.png|600]]

### Other cryptography protocol: One time pad
Before RSA, private key protocols were used. Both parties ($A$, $B$) need to **meet beforehand** to securely agree on the **shared private key**.

This shared private key can **both encrypt and decrypt** all information.

$A$ and $B$ agree on a binary of length $r=|\text{message}|$

$A$'s **encryption** function is then a bitwise **XOR** of the message:
$$
e(x)=x \oplus r
$$
The function is a bijection, and is its own inverse:
$$
e(e(x))=(x\oplus r)\oplus r=x\oplus(r\oplus r)\boxed{ =x }
$$

$B$ can apply the same function over the encrypted message to decrypt it.

For $r$ to be secure, $r$ needs to be **chosen at random**. If an attacker intercepts $e(x)$, all possibilities of $x$ are equally likely, and they get no information about $x$.

A major disadvantage of one time pad is that $r$ has to be **discarded** after each use. Otherwise, an attacker can listen to many messages and learn something about $r$.

>[!warning] One time pad is a toy cryptographic scheme.

### Other cryptography protocol: AES
Another private key scheme is the *Advanced encryption standard* (**AES**). It is widely used and very secure.

$A$ and $B$ have to agree on a random string $r$ of $128$ bits.
A bijection $e_{r}(\cdot)$ is specified from 128-bit strings to 128-bit strings.

Here, the encryption function $e_{r}(\cdot)$ **can be used repeatedly**. The only downside to RSA is that $A$ and $B$ have to meet beforehand and agree on the random string.

### RSA Bijection
RSA needs **encryption** and **decryption** functions, which are inverses of each other.

Let the message between $A$ and $B$ be numbers $\bmod N$. 

The encryption is a bijection on $\left\{ 0,1,\dots,N-1 \right\}$, which can be constructed as follows:

Pick any **2 primes** $p$ and $q$. Let:
$$
N=pq
$$
For every integer $e$ with $\text{gcd}(e, (p-1)(q-1))=1$, then
- the mapping $x\mapsto x^{e}\bmod N$ is a bijection on $\left\{ 0,1,\dots,N-1 \right\}$
- the inverse mapping, $d$ is the inverse of $e\bmod (p-1)(q-1)$ 

For all $x \in \left\{ 0,1,\dots, N-1 \right\}$, 
$$
{(x^{e})^{d}}\equiv x \bmod N
$$

Now:
- The **public key** is $e$
- The **private key** is $d$

For an attacker to decrypt messages, they need to find $d$. To do so, they need to know $p$ and $q$, which involves factoring $N$. For $p$ and $q$ large enough, this can be very difficult. 

### RSA Example
In this example, let $p=5$ and $q=11$, then:
$$
N=pq=(5)(11)=55
$$

Choose an *encryption exponent* $e$ that satisfies:
$$
\text{gcd}(e,(p-1)(q-1))=1\implies \text{gcd}(e,40)=1
$$
Many such $e$ will do. In this case, we will choose $\boxed{ e=3 }$.

Using the [[5_Euclids Algorithm#Extension to Euclid's Algorithm|extended Euclid's algorithm]] to find
$$
d=3^{-1}\bmod 40
$$
In this case:
$$
(3)(27)\equiv 1\bmod 40 \implies \boxed{ d=27 }
$$

Now, for any number $x\bmod 55$,
$$
y=x^{e}\bmod 55 \implies \boxed{ y=x^{3}\bmod 55 }
$$
For any encrypted number $y$,
$$
x=y^{d}\bmod 55 \implies \boxed{ x=y^{27}\bmod 55 }
$$

### Proof of RSA
This is the proof that RSA gives back **the original message** after encrypting and decrypting.

The mapping $x\mapsto x^{e}\bmod N$ is invertible, therefore it is a bijection. $e$ is invertible modulo $(p-1)(q-1)$ because $\text{gcd}(e, (p-1)(q-1))=1$.

We need to show that
$$
(x^{e})^{d}\equiv x \bmod N
$$

The exponent $ed \equiv 1\bmod (p-1)(q-1)$, and therefore we can write:
$$
ed=1+k(p-1)(q-1)
$$
for some $k$.

Now we need to show that
$$
x^{1+k(p-1)(q-1)}\equiv x\bmod N
$$
which would prove the statement prior.

In the left side of our equation, we can rewrite and take it $\bmod p$:
$$
\begin{align}
x^{1+k(p-1)(q-1)} \equiv & \,\, x\cdot (x^{p-1})^{k(q-1)}\bmod p \\
\equiv & \,\, x\cdot 1 \bmod p
\end{align}
$$
We know that $x^{p-1}\equiv 1 \bmod p$ due to [[6_Primality Testing#Fermat's little theorem|Fermat's little theorem]].

This shows that:
$$
x^{1+k(p-1)(q-1)} \equiv x \bmod p
$$
and for the same reasoning also:
$$
x^{1+k(p-1)(q-1)} \equiv x \bmod q
$$
Since $N=pq$ and both $p$ and $q$ divide $x^{1+k(p-1)(q-1)}-x$, then:
$$
\boxed{ x^{1+k(p-1)(q-1)} \equiv x \bmod N }
$$

