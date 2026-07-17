Lectures 6 & 7

## ASCII
ASCII stands for *American Standard Code for Information Interchange*. 

It defines **127 characters**, including:
- space
- basic punctuation
- 0-9
- A-Z
- a-z
- 32 control characters, including null (`\0`), tab (`\t`), newline (`\n`)

With only 127 characters, we can represent ASCII characters in **7-bits**. Computers can use **a single byte** for each ASCII character.

### Non-English Character Set
To accommodate non-English characters, **extensions** were created to ASCII, called a **character set**, such as:
- `ISO-8859-1` for Western European languages (ASCII + characters like é, ñ, £)
- `ISO-8859-7` for Greek characters (ASCII + α, β, γ, …)

Only **one character set** can be used at a time. Mixing languages like French and Greek is not possible.

In C, the data type `char` only uses a single byte, and can only hold ASCII and extensions to it.

Other languages that need more than 8 bits per character, such as Chinese and Japanese, have **their own standards**. These can't be mixed.


---
## Unicode
Unicode is created to address the incompatibility. Unicode can represent **every form of written communication** (~160,000 currently defined) in one character set.

There are many ***character encodings*** or ways to turn numbers into Unicode. For example, the `UTF-32` encoding takes 32 bits for each character. This is simple, but **very expensive** (4x the size for English only texts).

The `UTF-16` encoding takes 16 bits for many characters, and take 32 bits for characters beyond that limit. However, this is easy to get wrong, since many programmers assume 2 bytes = 1 characters, and will **break things like emojis**.

### UTF-8
The `UTF-8` encoding is much more clever. Each character dynamically takes **as little as 1 byte** and **as large as 4 bytes**.

`UTF-8` breaks the character numbers up by the number of bits needed to represent, padded as follows:

| Number of bits | Byte 1      | Byte 2      | Byte 3      | Byte 4      |
| -------------- | ----------- | ----------- | ----------- | ----------- |
| $1-7$          | `0xxx xxxx` |             |             |             |
| $8-11$         | `110x xxxx` | `10xx xxxx` |             |             |
| $12-16$        | `1110 xxxx` | `10xx xxxx` | `10xx xxxx` |             |
| $17-21$        | `1111 0xxx` | `10xx xxxx` | `10xx xxxx` | `10xx xxxx` |

Replace the `x`'s by the [[1_Integers#Unsigned Counting|unsigned]] binary representation of the integer, padded by $0$'s if needed.

When we parse a `UTF-8` text, we can immediately know **how many following bytes** belong to the same character, and parse accordingly.

Using UTF-8, ASCII characters are still represented with one byte. This means that all ASCII text is **also UTF-8 text**.

> [!warning] Note
> While C treats a `char` as one byte, an array of byte $\neq$ array of characters. For example, encoding:
> ```html
> <title>你好</title>
> ```
> This is 17 characters, but takes 21 bytes to encode in UTF-8.

For example, if we want to `UTF-8` encode the character 是, which is Unicode $26159_{10}$ or $0110\,0110\,0010\,1111_{2}$.

Since this needs 15 bits, we use the template from the third row, and this is encoded as:
```
[1110] 0110   [10]01 1000   [10]10 1111
```

If we try decoding this binary, we get:
$$
\begin{align}
1110\,0110\,1001\,1000\,1010\,1111_{2} & =\text{E6}\,\text{98}\,\text{AF}_{16}
\end{align}
$$
```python
>>> b'\xE6\x98\xAF'.decode('utf-8')
'是'
```


### Declaration
If we are working with text in a user-facing way, Unicode support should be considered **non-negotiable**. 

There is often a default encoding, but there is no guarantee that it is the right one. Some text based formats have **declaration of character encoding**, for example:

```http
Content-Type: text/plain; charset=utf=8
```

```xml
<?xml version="1.0" encoding="utf-8"?>
```

```html
<meta charset="utf=8" />
```

```css
@charset "utf-8";
```

