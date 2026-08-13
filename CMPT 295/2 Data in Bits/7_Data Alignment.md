Lecture 19

## Endianness
The 32-bit [[1_Integers|integer]] $12345678_{16}$ is 4 byte long: `0x12` `0x34` `0x56` `0x78`. However, for most computers these bytes are stored **backwards**: `0x78` `0x56` `0x34` `0x12`.

This order of storing puts the *least significant* bits first, and higher order last. Most computers are **little endian**.

Only some computers are **big endian**. The endianness is just a choice of the architecture, and are both reasonable.

We can usually ignore endianness, but we have to care about it when we are storing or transmitting **multi-byte values** to correctly interpret them.

If we are receiving a "*32-bit unsigned integer*" over network, we really should know if it is being transmitted in **big endian or small endian**.

### Byte order mark
In [[2_Characters#Unicode|UTF-32]], characters can be encoded as **UTF-32LE** for little endian and **UTF-32BE** for big endian.

Unicode also has another way to break the ambiguity. The character "*zero width no-break space*" takes up **no space** and has the character number $\text{FEFF}_{16}$. This character is included as the first character in the stream to make the **endianness detectable**.


---
## Alignment
When storing values in memory, there ***can*** be speed penalty if the data is not **aligned**. Generally, a value is aligned when the memory address is divisible by its size. For example, a 64-bit integer is aligned if the [[1_Memory#Pointers|pointer]] is divisible by 8 (bytes).

In [[5_SIMD|SIMD]] there are instructions specifically for aligned data, such as `movdqa` (aligned) and `movdqu` (unaligned).

In modern processors, there is not a clear difference between aligned and unaligned. We can also **assume everything is unaligned** and move on.

The x86 [[2_Registers#Calling Convention|calling convention]] requires that the [[5_Stack#Stack pointer|stack pointer]] is 16-byte aligned when a function is called, but we can also ignore it.

### Padding
The compiler tries as hard as it can to get any speed benefit possible. In C/C++, structs and classes are **automatically aligned** as they are laid out in memory, and they are stored in the **same order** as they are defined.

If we have a struct:
```c
typedef struct {
	uint32_t a;
	uint8_t b;
	uint32_t c;
	uint8_t d;
} stuff;
```

The compiler will want `a` and `c` to be 32-byte aligned. 24-byte paddings will be added to `b` and `d` to achieve that goal.

In Rust, values may not be stored in the same order, but they **will be aligned**. This allows for smaller required padding.

