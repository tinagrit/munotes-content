Lecture 8

## Bit field
A boolean value takes **1 bit** to represent yes/no true/false. A **bit field** is an arrangement of these boolean.

For example, if we have:
```python
bool1 = 1
bool2 = 0
bool3 = 0
bool4 = 1
```

We can store all of them in one 4-bit [[1_Integers#Unsigned Counting|integer]] as a bit field, where **each position** in the field holds a boolean:
```python
my_field = 0b1001
```

We can now use [[3_Bit Masking#Bit mask|bit masking]] to **select** the data we want. For example, if we want `bool3`, we can do:
```c
my_field & 0b0010
```
since `bool3` is on the third position.

Instead of using the binary literal every time, we can use the [[1_C and Assembly#Preprocessing|C preprocessing]] to define the boolean locations:
```c
#define BIT_FIELD uint4_t
#define BOOL1 0b1000
#define BOOL2 0b0100
#define BOOL3 0b0010
#define BOOL4 0b0001
```

In assembly, the GNU [[1_C and Assembly#Assembling|assembler]] accepts definitions like this:
```nasm
.equ BOOL1, 0b1000
.equ BOOL2, 0b0100
.equ BOOL3, 0b0010
.equ BOOL4, 0b0001
```


### Checking a bit
Use the defined constant to bit mask the position.

In C, using the C preprocessing definition above, to access `bool3` we can do:
```c
my_field & BOOL3
```

In assembly, using the GNU assembler definition above, given that the bit field is in `%rdi`, to access `bool3` we can do:
```nasm
test $BOOL3, %rdi
jz value_is_false
```


### Setting a bit
To set a bit to `1`, use the defined constant to `OR` with the bit field.

`OR`ing anything with `1` results in `1`. 
Therefore, if we want to set `bool3` to `1`, no matter what the bit field is, `OR`ing the field with `0b0010` will turn `bool3` into `1`.

![[chart19.png|400]]

In C, to set `bool3` we can do:
```c
my_field |= BOOL3
```

In assembly, given that the bit fields is in `%rdi`, to set `bool3` we can do:
```nasm
or $BOOL3, %rdi
```


### Clearing a bit
To set a bit to `0`, **negate** the defined constant to `AND` with the bit field.

`AND`ing anything with `0` results in `0`.
Therefore, if we want to set `bool3` to `0`, we can `AND` the field with `0b1101` to clear out the third position, without modifying the rest.

![[chart20.png|400]]

In C, to clear `bool3` we can do:
```c
my_field &= ~BOOL3
```

In assembly, given that the bit fields is in `%rdi`, to clear `bool3` we can do:
```nasm
mov $BOOL3, %rax
not %rax
and %rax, %rdi
```

