Lectures 3 & 4

## The Stack
The stack lives **on the memory**. The data structure handles `push` and `pop`.
- `push` adds a value at the **top** of the stack
- `pop` returns the value at the **top** of the stack

![[Screenshot 2026-05-30 at 3.09.49 PM.png|400]]

If we push, in order, `1 2 3 4 5`, the order that popping will return is `5 4 3 2 1`.

In assembly, we can `push` any value to the stack, then `pop` it to any [[2_Registers#Registers|register]].

```nasm
push %rax
pop %rbx
```
Here, the value of `%rax` is added to the stack, and immediately returned to `%rbx`. This is basically an inefficient way to copy `%rax` to `%rbx`.

### Stack pointer
The stack is managed by the `%rsp` [[2_Registers#Call Preservation|call-preserved]] register, which holds the memory **address** at the **top** of the stack.

In assembly, we can use `()` around a memory address to **get the value** at that memory location (*like dereferencing in C*). We can put a number before the brackets, like `8()`, to locate the value of that many **bytes after** the location.

Since `%rsp` holds the address to the top of the stack, we can get the value of the first item in the stack with `(%rsp)`, the second item with `8(%rsp)`, the third item with `16(%rsp)`, and so on. This is assuming one item is 64 bits.

![[chart10.png|500]]

Since the stack lives at the **top of the memory space**, the top of the stack goes **down** as things are pushed in.

![[chart11.png|700]]

When `push` is called in assembly, the top of the stack is subtracted. This is done within `push`:
```nasm
sub $8, $rsp
```

The stack is also how `call` and `ret` work. The address of where to return to is on the stack.

`call f` is essentially:
```nasm
push %rip
jmp f
```
where `%rip` is the **instruction pointer**.

`ret` is essentially:
```nasm
pop %rip
```


### Preserving data
In assembly, when we use [[2_Registers#Call Preservation|call-preserved]] registers, we need to make sure to return the original value back in. We can **use the stack** for preservation.

For example, `%r12` is a preserved register. We can do:
```nasm
push %r12
# ... use %r12 to do calculations
pop %r12
ret
```

We can also use the stack to preserve non call-preserved registers. When we **call a function**, the function may modify any non-preserved registers. For example, if we need to use `%rdi` after calling `f`:
```nasm
push %rdi
call f
pop %rdi
# ... use %rdi
```


### Local Stack Variables
There is a limited number of registers available. If we need more, we can use **the stack**, up to **8 MB** in Linux.

When using these stack variables, we can use `()` on the [[#Stack pointer]] directly.

For example, writing this function:
```c
int64_t foo(int64_t x, int64_t y) {
	int64_t a = x;
	int64_t b = y;
	a += b;
	b *= a;
	return b;
}
```

We can do:
```nasm
foo:
	push %rdi
	push %rsi
	
	# Now, 8(%rsp) = a and (%rsp) = b
	
	mov (%rsp), %rax
	add %rax, 8(%rsp)
	
	imul 8(%rsp), %rax
	
	add $16, %rsp # Delete everything from the stack
	ret
```

Notice that we only used `%rsp` and `%rax` after the first two `push`.

This is what the compiler does with `-O0` flag, i.e., no optimization of C code.


### Recursion
With local stack variables and conditional jumps, we have **everything we need** for recursion.

For example, this C factorial function:
```c
uint64_t factorial(uint64_t n) {
	if (n == 0) return 1;
	
	return n * factorial(n-1);
}
```

We can do the following in assembly:
```nasm
factorial:
	test %rdi, %rdi
	jne factorial_recursive
factorial_base:
	mov $1, %rax
	ret
```

This **checks** if the argument is `0`, if it **is zero**, then it would continue to `factorial_base` and return `1`. If it is **not zero**, then it would jump to `factorial_recursive`.

```nasm
factorial_recursive:
	push %rdi         # push n to stack
	sub $1, %rdi      # n' = n-1
	call factorial    # rax = factorial(n')
	pop %rdi          # restore original n
	mul %rdi          # rax *= n
	ret
```

