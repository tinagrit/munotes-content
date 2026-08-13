Lectures 18-19

## Threads
A **process** is an instance of a running program. A process has some memory allocated to it. The OS deals with allocating resources to multiple processes at once.

A process may have one or more **threads**. While all threads in the process share the same memory, each thread has its own [[2_Registers#Registers|registers]], [[5_Stack#The Stack|stack]], and [[3_Processor#Instruction Cycle|instruction pointer]]. 

The OS also makes sure that all threads get processor time, it can start/stop/move threads as it wants. [[3_Superscalar Processing#Superscalar Processors|Superscalar processors]] can run multiple threads in the **same core**. There could be more threads than logical cores, and the OS would force them to **take turns**.

### Thread safety
Threaded code is *generally* difficult to write, since it **can be unpredictable**. However, we can avoid the hardest part about threads.

Threads may be paused at any time by the OS, so if we have one set of **data shared** by two threads, thread 1 might be paused in the middle of the update, and thread 2 can start executing. This leads to issues like incomplete data and overwriting.

Multiple threads are easy if we can guarantee that for each data:
- it is **available** (read/write) to only **one thread**, or
- it will not be **modified** by **any thread**, or
- using a language specific thread safe channel, like Java's `BlockingQueue`

### C++ Threads
In C++, we can use  `std::thread` to create threads. For example, if we have a function:
```cpp
void say_hello(int id) {
	cout << "Hello from thread " << id << "\n";
}
```

We can start three threads, each one running the defined function:
```cpp
auto t1 = std::thread(say_hello, 1);
auto t2 = std::thread(say_hello, 2);
auto t3 = std::thread(say_hello, 3);
```

and wait for them to finish (blocking):
```cpp
t1.join();
t2.join();
t3.join();
```


We can also use `std::async` to call a function in a new thread and **get a return value**. The return value will be a `std::future`, which is a result that will be ready some time in the future. When we want to use the result, it will wait until the results are avilable.


For example, if we have this function:
```cpp
int add(int a, int b) {
	return a + b;
}
```

We can call async:
```cpp
std::future<int> f1 = std::async(add, 6, 7);
```

Then when we need the result, we can do:
```cpp
cout << f1.get() << '\n';
```

