Lectures 12 & 13

## Measuring time
There are many ways to time a code, and the complexity of [[3_Processor#The Processor|modern CPUs]] only makes it complex to time one.

### Measuring cycles
The x86 time stamp counter counts the **number of CPU** [[3_Processor#Instruction Cycle|cycles]] since the core was reset.

This is not the best way to measure running time, since there is **no guarantee** that each core will have a synchronized counter. If the code is moved between cores, the *start* and *end* might be unrelated.

The cycle count can also depend on **power state** of the core. At power saving, the core will execute slower than at full speed.

The counter is accessible with the `rdtsc` (*read time-stamp counter*) instruction. It is also accessible with the `__rdtsc()` [[6_Compiler Optimization#Intrinsics|intrinsic]].

```c
#include <x86intrin.h>
```
```c
unsigned start = __rdtsc();
result = calculate_something();
unsigned end = __rdtsc();
unsigned elapsed = end - start;
```

### Measuring real time
A better way to measure runtime is to look at real elapsed time. The C function `clock_gettime()` will get the time at a **nanosecond** resolution.

There are two options for `clock_gettime`:
- `CLOCK_PROCESS_CPUTIME_ID` will get the **CPU time**. If there are 3 threads running at full speed, it will progress 3 seconds for every real second elapsed.
- `CLOCK_REALTIME` will get the **real time**.

```c
#define _POSIX_C_SOURCE 199309L
#include <time.h>
```
```c
struct timespec start, end;
clock_gettime(CLOCK_PROCESS_CPUTIME_ID, &start);
result = calculate_something();
clock_gettime(CLOCK_PROCESS_CPUTIME_ID, &end);
double elapsed = (end.tv_sec - start.tv_sec) + (end.tv_nsec - start.tv_nsec) / 1e9;
```

Make sure to only measure the parts we care about, i.e. the actual calculation, not the setting up.

If the CPU is running at a slower low-power mode, it might need **some warmup code** to get it to run at full power. If the CPU is overheating (usually around 99 C), it may **thermal throttle** and slow itself down to avoid damage.

### Measuring whole program
While timing the whole program can measure parts we don't want, such as setting up, it will flexibly work on **any program**.

This is accessible with the Linux's `time` command:
```shell
$ time ./a.out
real    0m1.714s
user    0m1.389s
sys     0m0.114s
```

For example, this is 1.714 seconds of elapsed clock time, 1.389 seconds of processor time, and 0.114 waiting on the [[1_Memory#Syscalls|system calls]].


---
## Perf
The `perf` tool in Linux gives a lot of **stats** about what's going on in the program. It is tied to the kernel, and not available in virtual machines.

`perf list` lists everything that `perf` can measure, and we can select what to measure using the `-e` flag.

For example, to measure [[2_Branch Hazards#Branch Hazards|branch misses]], we can do:
```shell
$ perf stat -e branches,branch-misses ./a.out
Performance counter stats for './a.out':

       451,838,503      branches
           945,485      branch-misses

       0.711910230 seconds time elapsed
```

The relevant measurements in this course includes:
- `L1-dcache-loads` [[1_Memory#Cache|L1 cache]] loads
- `L1-dcache-load-misses` L1 cache misses
- `LLC-loads` Last level cache loads
- `LLC-load-misses` Last level cache misses
- `branches` number of branches
- `branch-misses` number of branch misses
- `instructions` number of [[3_Processor#Instructions|instructions]]
- `cycles` number of CPU [[3_Processor#Instruction Cycle|cycles]]

### Perf on running process
If we know the **PID** (*process ID*), we can start `perf` on an already-running process using the `-p` flag.

```shell
$ perf stat -e branches,branch-misses -p 12345
```

A Linux process or CPU monitoring tool can tell the PID of any running program, or within C, we can use `getpid()` to return the PID of the current code.

```c
printf("pausing, start perf now on pid: %u\n", getpid());
sleep(10);
...
printf("stop perf now\n");
sleep(10);
```

### Record perf to a file
`perf` can provide more details to the analytics when recording. Use the debugging symbol `-g` when compiling, then use:

```shell
$ perf record -e branches,branch-misses ./a.out
```

To explore the recorded data:
```shell
$ perf report
```

Use these keybinds to navigate `perf report`:
- `↑` `↓` to move around
- `enter` to descend an option
- `esc` to move back out
- `a` to annotate code
- `t` to switch between percent/total

The **annotation** would show the analytics **line-by-line**. The counters are associated to the lines *close* to when the event occurred.

It is recommended to use `-O0` instead of `-O3` since higher optimization modify a lot of things and the code gets more difficult to read.


---
## Valgrind
Valgrind provides analytics related to memory leak, cache misses, and instruction counts.

By default, it looks for memory leak problems:
```shell
$ valgrind ./a.out
==2923447== HEAP SUMMARY:
==2923447==     in use at exit: 0 bytes in 0 blocks
==2923447==   total heap usage: 3 allocs, 3 frees, 51,201,024 bytes allocated
==2923447==
==2923447== All heap blocks were freed -- no leaks are possible
```

### Cachegrind
Cachegrind reports cache performance in the following format:

```shell
$ valgrind --tool=cachegrind --cache-sim=yes ./a.out
==2933165== I   refs:      602,938,883Instructions
==2933165== I1  misses:          1,530
==2933165== LLi misses:          1,517
==2933165== I1  miss rate:        0.00%
==2933165== LLi miss rate:        0.00%
==2933165==
==2933165== D   refs:      258,000,928  (173,577,018 rd   + 84,423,910 wr)
==2933165== D1  misses:     10,164,053  (  9,115,035 rd   +  1,049,018 wr)
==2933165== LLd misses:      5,798,679  (  4,749,697 rd   +  1,048,982 wr)
==2933165== D1  miss rate:         3.9% (        5.3%     +        1.2%  )
==2933165== LLd miss rate:         2.2% (        2.7%     +        1.2%  )
==2933165==
==2933165== LL refs:        10,165,583  (  9,116,565 rd   +  1,049,018 wr)
==2933165== LL misses:       5,800,196  (  4,751,214 rd   +  1,048,982 wr)
==2933165== LL miss rate:          0.7% (        0.6%     +        1.2%  )
```

`D1` refers to L1 cache data, and `LLd` refers to the last level cache data. Both are measuring the whole program, like `perf stat`.

Valgrind can also **annotate**, and show the analytics **line-by-line**. 

```shell
$ cg_annotate cachegrind.out.12345
```

Note that Valgrind **slows down** code execution. It counts memory access as accurately as possible, but will not be a good performance indicator.

### Callgrind
Callgrind measures the number of times each instruction runs, and will show **which part** of the code **takes time** during execution.

It will report per-function and tells us how many times it was called, or how much time execution spent in that code.

```shell
$ valgrind --tool=callgrind ./a.out
$ callgrind_annotate callgrind.out.12345
```

