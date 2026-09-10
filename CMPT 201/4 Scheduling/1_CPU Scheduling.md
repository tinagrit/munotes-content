Lecture 4

## CPU Scheduling
One CPU core can run **many** [[1_Processes#Processes|processes]]. Scheduling helps to **share** the core.

For many [[2_Scheduling Algorithms#Scheduling Algorithms|scheduling algorithms]], one process **cannot hog the entire core** forever. If the task is extensive, at one point, the CPU will have to stop working on it and let other processes get their work done too. This will require **context switching**.

> [!tip] Context switch
> CPUs may have to do a *context switch*, by **stopping one process** entirely and **starting/resuming another** process.
> 
> There is a cost to context switch, and therefore doing this frequently is not ideal.

### Ready and I/O queue
The CPU tries its best to keep busy, and always have something to work on. There are two queues where process work can be put in.

- **Ready queue**: work waiting for CPU to start executing
- **I/O queue**: [[1_File Syscalls#File Syscalls|Input/output syscalls]] waiting to start

When a user launches a process, it gets added to **the ready queue**. 
At one point, the scheduler will pick this process out of the queue to start executing. 
If the process ever needs an I/O, it will be added to **the I/O queue**, and the CPU will work on something else until that I/O is done, and the process gets added back to **the ready queue**.

![[chart13.png|700]]

### Scheduler
The scheduling algorithm finds **the best way** to pick a process out of **the ready queue**.

These are the criteria that a scheduler needs to meet:
- Maximize:
	- **CPU utilization**: keep the CPU as busy as possible
	- **Throughput**: number of work done per time
- Minimize:
	- **Turnaround time**: time it takes to complete 1 work
	- **Waiting time**: time a process needs to wait in the ready queue
	- **Response time**: time between request and first response

