Lecture 4

## Scheduling Algorithms
There are two types of scheduling algorithms
1. **Preemptive** - can stop a [[1_Processes#Processes|process]] at any time to start another
2. **Non-preemptive** - will not stop a process, only when it finishes or when it is waiting for something that takes a long time

### First Come First Served (FCFS)
- Non-preemptive
- Runs in the order of arrival
- Long processes can sabotage every other process

For example: P1, P2, P3 arrive around the same time, but are in the [[1_CPU Scheduling#Ready and I/O queue|ready queue]] in this order.

![[chart14.png]]

The waiting time are:
- **P1**: $0$
- **P2**: $24$
- **P3**: $27$

The average waiting time is $\dfrac{0+24+27}{3}=17$

### Shortest Job First (SJF)
- Non-preemptive
- Among the remaining processes, pick the one with the shortest execution time first
- Need to know how long a process will take

For example: P1, P2, P3, P4

![[chart15.png]]

The waiting time are:
- **P1**: $0$
- **P2**: $6$
- **P3**: $3$
- **P4**: $7$

The average waiting time is $\dfrac{0+6+3+7}{4}=4$

### Shortest Remaining Time First (SRTF)
- Preemptive
- Schedule the process with the shortest ***remaining*** execution time
- Need to know how long a process will take

For example: P1, P2, P3, P4

![[chart16.png]]

The waiting time are:
- **P1**: $0$
- **P2**: $0$
- **P3**: $0$
- **P4**: $2$

The average waiting time is $\dfrac{0+0+0+2}{4}=0.5$

### Round Robin
- Preemptive
- Pick the next process in the ready queue, and **run it for** $x$ **seconds** (*the quantum*), the put it back at the bottom of the queue
- If the quantum is too long, it is essentially first come first served, if it is too short, the context switching will be too expensive

For example: P1, P2, P3, P4

![[chart17.png]]

The waiting time are:
- **P1**: $0$
- **P2**: $0$
- **P3**: $2$
- **P4**: $4$

The average waiting time is $\dfrac{0+0+2+4}{4}=1.5$

### Priority Scheduling
- Preemptive or non-preemptive
- Pick the **highest priority** process in the ready queue and run it
- A priority is typically a **number** (lower is higher priority)

> [!tip] Starvation
> Priority scheduling could lead to starvation, where low priority processes may never run.

### Multilevel Queue Scheduling (Weighted RR)
- Combination of [[#Priority Scheduling]] and [[#Round Robin]] to avoid starvation
- There are many ready queues
	- **System queue**: priority 0
	- **Foreground queue**: priority 1
	- **Background queue**: priority 2
- Each queue gets CPU time based on its priority
- For example, the CPU could execute from `0` `1` `2` `0` `1` `0` `0` `1` `2` `0` `1` `0` `0`  `1` `2` `0` `1` `0` ...
- We use another scheduling algorithm (like FCFS, RR) to choose a process from the subqueue (Priority `1` gets to run but which process in priority `1`?)

### Multilevel Feedback Queue Scheduling
- Similar to [[#Multilevel Queue Scheduling (Weighted RR)]], we have 3 queues
	- **Q0**, **Q1**, **Q2**
- Processes start in **Q0** and get to run for $x$ seconds. If it is not done, move to **Q1**.
- All of **Q0** is cleared before **Q1** is executed. Processes in **Q1** then get to run for $y$ seconds. If they are still not done, move to **Q2**.
- All of **Q1** is cleared before **Q2** is executed. **Q2** uses [[#First Come First Served (FCFS)]]

> [!tip] Process aging
> The procedure to lower the priority of a process if it takes too long is called **process aging**.

### Linux Completely Fair Scheduler (CFS)
- Two *classes*/types of processes
	- **Real-time** processes (priority 0-99)
	- **Normal** processes (priority 100-139)
- Linux uses the `nice` value to assign a priority to normal processes
	- `nice` can be from $-20$ to $+19$, where "less nice" means "higher priority"
	- `nice` is defaulted to $0$
	- `nice` of $-20$ means priority 100, and `nice` of $+19$ means priority 139
- Sorts all processes by their **execution time**. The longer it ran, the less chance it gets to run. All processes get roughly similar CPU time.
- Execution time uses **virtual run time**, calculated using the physical run time and a formula in terms of priority

