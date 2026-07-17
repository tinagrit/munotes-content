Lecture 11

## Data Pipeline
Modern processors have **pipelines** or *are pipelined*. 

Recall the [[3_Processor#Arithmetic Logic Unit (ALU)|Arithmetic Logic Unit]] and surrounding circuitry. The [[3_Processor#Clock signal|clock signal]] would synchronize when the ALU finishes calculation and puts the result into a registry, so that it can be read.
- We want the clock signal to **be fast**, so that we could do more in the same amount of time
- We also want instructions to **be simple** enough, so that it could be done within a clock signal

A solution to this is to **pipeline the data**. If an instruction takes too long, we can break it up into multiple steps, and let those steps happen across multiple cycles.

![[Screenshot 2026-07-16 at 4.56.29 PM.png|250]]

For 4 ALUs in a pipeline as shown, there could be **4 calculations** in progress for **at any moment**. Instructions follow each other through the circuit like a conveyor belt.

![[Screenshot 2026-07-16 at 4.59.28 PM.png|300]]

Modern processors like [[1_C and Assembly#Running a C code|Haswell]] have pipelines with [[3_Superscalar Processing#Superscalar Processors|14-19 stages]]. Other modern processors have similar pipeline lengths.

### Data Hazards
Data pipeline is good when each instruction is independent from one another. For example,

```nasm
mov $3, %rax
add %rbx, %rcx
imul $12, %rdx
```

Here, each instruction touches a different set of [[2_Registers#Registers|registers]]. Therefore, when the first instruction (`mov`) is down the pipeline and **not yet done**, the next instruction (`add`) **can already start**.

This will become a problem when instructions **depend on the result** from a previous instruction. For example,

```nasm
mov $3, %rax
add %rax, %rcx
imul $12, %rcx
```

Here, the second instruction (`add`) **cannot start** until it knows what `%rax` is after the first instruction (`mov`). This is a **data hazard**. 

In a processor, if an instruction needs a result that's mid-calculation, **just pause** until that data becomes available. This is called a **stall** or **putting a bubble** into the pipeline.

The stall **doesn't have to be the full length** of the pipeline. Parts of the instruction (like fetching and decoding the instruction) can be done without depending on previous calculations.

### Out of Order Execution
Stalling the pipeline slows down execution. Processors will **look ahead** for instructions that don't depend on previous calculations, can **start those early**.

