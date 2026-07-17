Lecture 12

## Superscalar Processors
Processors chain many [[3_Processor#Arithmetic Logic Unit (ALU)|Arithmetic Logic Units]] into a [[1_Data Hazards#Data Pipeline|Pipeline]]. Modern CPUs have many of these pipelines, called **execution units**. 

Each unit can work on an instruction separately. A processor with multiple execution units is **superscalar**.

These execution units can be **specialized**, each one doing a certain **type** of operation. For example, many can do most integer operations, but only one for multiplication, several for floating point, one for [[2_Memory in Assembly#Loading pointer|lea]] operations. The processor **decides on its own** to utilize these execution units, and the programmer doesn't have to do anything.

This is all within **one core**, which means processors can complete **> 1 instruction** per cycle. 

### Simultaneous Multithreading (SMT)
Superscalar processors allow a **single CPU core** to work on **multiple threads** concurrently.

A **thread** is execution happening within a program. Each thread has its **own collection of registers** and can get work done mostly independently of other threads. A process can have one or many threads.

If conditions are right, SMT can run **two threads** at full speed on a single CPU core, by utilizing unused execution units.

Processors with SMT will have more **logical cores** than **physical cores**. For example, `lscpu` may describe such system as:
```sh
CPU(s):               8
⋮
Core(s) per socket:   4
```

This is one more reason why the performance of real code is difficult to predict/measure.

---
## Heterogeneous Cores
Some modern processors have multiple cores that are **not identical**. These cores usually implement the same instruction set, but with **different performance**.

There are **slower cores** that use **less power**, so if there is not much computation happening, these cores can work to **save power and battery**. Slower cores can involve slower clock speed, fewer execution units, less cache, no hyperthreading, etc.

This is, again, **not a concern** for the programmer. The OS and the processor will assign instructions and threads to what is appropriate. 