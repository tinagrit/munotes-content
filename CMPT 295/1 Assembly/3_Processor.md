Lectures 2, 19

> [!tip] Aside
> This note is not about assembly, but about how wires and circuits can come together to build a processor that takes instructions and execute them.

## Digital Circuits
The use of **binary** in electrical circuits where *low* voltage represents a 0, and *high* voltage represents a 1.

Each value is called a **bit**. `1` is a bit. `0110` is 4 bits.
A bit is abbreviated with "b".

A collected of 8 bits is called a **byte**. `01101100` is a byte.
A byte is abbreviated with "B".

### Transistors
A circuit **junction** that switches the through current on or off.

For example, in this transistor:
![[Screenshot 2026-05-23 at 2.29.11 PM.png|150]]

Only if there is a current on **B**, then **C-E** would be connected.

In a modern processor, there are over **50-150 billion** transistors.

### Logic gates
We can hook up multiple transistors to make **logic gates**. 

For example, if we build transistors like this:
![[Screenshot 2026-05-23 at 2.31.50 PM.png|250]]

This will become and `AND` gate, where there will only be current through **C** if there is current on **both A** and **B**.

Any logic gate can be built with transistors (`AND`, `OR`, `NAND`, `NOR`). 

Using these gates, we can build a circuit to implement **any combinatorial logic**. These are logic functions where the output depends only on the current inputs, no state or memory.


---
## The Processor
The number of bits we want to work with at a time is called the **word size**. In the examples below, our word size is 8-bit (1 byte).

In the modern [[2_Registers#Writing assembly|x86-64 architecture]], the word size is **64-bit**. Older CPUs work with 32- and 16-bit word sizes.

Modern 64-bit processors can easily do calculations on values smaller than their word size. Instructions tell it what to do:
```nasm
add %rcx, %rax  # 64-bit add
add %ecx, %eax  # 32-bit add
add %cx, %ax    # 16-bit add
add %cl, %al    # 8-bit add
```

### Multiplexer
The multiplexer **selects** which value to output, based on the **SEL** (selection) value. For example,

![[chart03.png|400]]

In this multiplexer, **OUT** will be:
- the same value as **A** if **SEL** is `1`
- the same value as **B** if **SEL** is `0`

### Ripple adder
The ripple adder can **add**, **subtract**, and **bitwise add** integers. The integers are represented with bits.

This component is used to build a circuit that takes two 8-bit integers **A** and **B**, and output the three calculations.

![[chart04.png|400]]

### Arithmetic Logic Unit (ALU)
We can combine the **ripple adder** circuit with a **multiplexer**, and select which calculation we actually want.

The ALU is represented with this shape:
![[Screenshot 2026-05-23 at 2.48.24 PM.png|250]]

Where **S** is the 5-bit selection value, **A** and **B** are the two 8-bit integers, and **Z** is the output.

### Clock signal
A clock provides a **pulse** (alternating `1` `0` `1` `0` ...) to synchronize the circuit, acting like a metronome. 

A clock cycle needs to be long enough for the circuit to finish what it's doing.

When the clock signal changes from `1` to `0`, the edge is called the **falling edge**.
The opposite is called the **rising edge**.

![[Screenshot 2026-05-23 at 3.05.53 PM.png|400]]

### Flip flop
A flip flop is a **memory** circuit. Given a value, `1` or `0`, it can **remember** what the value is and return that same value when asked for.

If there is a **change** to the given value, the flip flop will update it, but not instantly. Flip flops update on the *falling edge* of the clock signal (when clock signal changes from `1` to `0`).

![[chart05.png|400]]

This is done so that we're sure the **correct results** are stored. To have a short clock cycle, we need simple circuit.

### Register
We can combine many flip flops to store **multiple bits**. If we have 8 flip flops, we can store a byte.

We can connect registers to an ALU, store the result of the calculation, and repeat.

![[Screenshot 2026-05-23 at 3.08.39 PM.png|350]]


---
## Instructions
We need to figure out the **S** inputs to the ALU, and also what to do with the output values.

Each operation the processor does is called an **instruction**, which the programmer will create.

These instructions are stored the in **instruction register** (IR). The size of the IR is the size of 1 instruction, in this case 16 bits.

Another circuit, the decoder, takes the instruction and turn it into control signals.
![[Screenshot 2026-05-23 at 3.53.22 PM.png|300]]

### Memory
The memory in modern computers is **DRAM** (*Dynamic Random Access Memory*). It consists of **capacitors** (like batteries) that hold charges and store data, as long as it is powered.

It is **too expensive** to have lots of registers, so we want lots of memory instead.

Memory is read/written at least 8 bits at a time. Each byte in memory is represented with an **address**.

A memory circuit looks like this:
![[Screenshot 2026-05-23 at 7.16.05 PM.png|300]]

To read data from memory, we set **WE** (write-enable) to `0` and input the **ADDRESS**. The memory should return the data in **DATA_OUT**.

To write data to memory, we set **WE** to `1`, input the **ADDRESS**, and input the data in **DATA_IN**.

The number of bits in **ADDRESS** determines how large can a memory be. For an 8-bit address, we can have up to $2^{8}=256$ memory locations. This is why a 32-bit CPU can only handle RAM up to 4 GB.

Both the data we work with and the program itself will be stored in memory. This is referred to as **Von Neumann architecture**.

### Instruction Cycle
To correctly read instructions from memory and pass them to the IR, we need another register: the **instruction pointer** (IP). This register holds the memory address for the *next* instruction to be executed.

For every instruction a processor runs, the IP is moved to the next location.

This entire process is called the **instruction cycle**, consisting of:
1. **fetching** the instruction from memory at IP to IR
2. **decoding** the instruction
3. **executing** the instruction
4. **incrementing** the IP


---
## Syscalls
The `syscall` instruction is a way to **ask the OS** to take over and do something for us. It is like a [[2_Registers#Calling Convention|function call]], but it will pause the process, then the OS kernel will do what we requested, then the process will be resumed.

The `syscall` instruction has no operand, but the syscall number has to be put in `%rax` before the instruction. 

For example, the syscall number for writing is `1`. It requires arguments:
- file descriptor (where to write) in `%rdi`. Writing to the terminal is `fd=1`
- the pointer to the start of the string in `%rsi`
- the number of bytes to write in `%rdx`

We can write to the terminal in assembly (see [[2_Memory in Assembly#Static memory in assembly|static memory]] and [[2_Memory in Assembly#Loading pointer|lea]]):
```nasm
.data
text:
	.ascii "some text to print\n"
text_len:
	.quad 19

.text
mov $1, %rax
mov $1, %rdi
lea text(%rip), %rsi
mov text_len(%rip), %rdx
syscall
```

There are many syscalls available. These are some of them:
- create a new directory `mkdir` - syscall `83`
- exit the process - syscall `60`
- change the data segment size - syscall `12` (this is what `malloc` and `free` uses)
