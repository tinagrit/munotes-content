Lecture 18

## Language Abstraction
Different programming languages provide different **instruction abstractions**, provided by a combination of language design and compilers.

Most languages other than C/C++ don't have raw pointers, or manual `free`/`delete`. However, overall interactions with the processor **should be similar**.

### Interpretation
Many languages are **interpreted** rather than [[1_C and Assembly#Compiling|compiled]], such as *Python, JavaScript, and Java*. These languages create **bytecode** as a low level representation of the logic, but not machine code. 

The bytecode is **interpreted** by a *virtual machine* at runtime, called a *just-in-time* (JIT) compile. A JIT can get basically the same performance as ahead of time compiled machine code in C.

### The for loop
While the `for` loop is a concept so core to programming, most of the time it is **not the right abstraction** for a "*do this to each element*" operation.

With problems like summing an array, the loop we do in C `for(i=0; i<len; i++)` has a few problems.
- It forces the order of algebra, even if we don't care
- There is a lot of *noise* in the code, many things we don't care about

```c
double total = 0.0;
for (int i=0; i<len; i++) {
	total += values[i];
}
```

In this code, we **care** about the accumulator `total = 0.0` and the operation `+` from the array `values`, but we **don't care** about the `for` loop, the index `i`, the comparison `i<len`, and the increment `i++`. We just want to sum the array.

Compare this to the iterator abstraction available in Rust.

```rust
values.iter().fold(0.0, |a,b| a.algebraic_add(b))
```

Here, there is a lot less noise. We operate on the array `values`, starting the accumulator with `0.0`, and add `a` and `b`.

The `fold()` method means to use the second argument function to combine values in an accumulator. The `|a,b| a.algebraic_add(b)` is an *anonymous function* that takes in arguments `a`,`b`, and returns `a.algebraic_add(b)`. This `algebraic_add()` method tells Rust to **not care about the order** of additions.

This is important especially for [[5_SIMD|SIMD]]. The compiler's [[6_Compiler Optimization#Auto-vectorization|auto-vectorization]] wouldn't work if there is a set order of addition to the floating point. By telling the compiler that it's ok for this function, it can help improve the performance.

Python has even better abstraction. For example, for the array summing problem:
```python
total = sum(values)
```

or if we want to do something more complex, like summing the squares of all positive numbers in the array, Python can do:

```python
total = sum(v*v for v in values if v > 0.0)
```

