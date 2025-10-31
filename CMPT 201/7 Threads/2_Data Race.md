

## Deterministic programs
- Desired program output
- Program runs **the same way** every time
- May have **different behaviour**, but the **order** of scheduled threads are the same
- Non-deterministic output result of a **race case**


## Race case
- a **Data race** problem when multiple threads **race** to update data and overwrite each other
- A **race condition** is a condition that specifies the timing/order of operations that the code will correctly run

For example, if two threads run `counter++` the following code, gets run:
```c
int tmp = counter;
tmp = tmp+1;
counter = tmp;
```

This should increment `counter` by 1 for each thread, but it depends on which thread runs each line first.

Case 1: in the end, `counter += 2`

| Thread 1             | Thread 2             | Values                             |
| -------------------- | -------------------- | ---------------------------------- |
| `int tmp = counter;` |                      | `counter: 1`<br>`thread1 > tmp: 1` |
| `tmp = tmp+1;`       |                      | `counter: 1`<br>`thread1 > tmp: 2` |
| `counter = tmp;`     |                      | `counter: 2`<br>`thread1 > tmp: 2` |
|                      | `int tmp = counter;` | `counter: 2`<br>`thread2 > tmp: 2` |
|                      | `tmp = tmp+1;`       | `counter: 2`<br>`thread2 > tmp: 3` |
|                      | `counter = tmp;`     | `counter: 3`<br>`thread2 > tmp: 3` |

Case 2: in the end, `counter += 1`

| Thread 1             | Thread 2             | Values                             |
| -------------------- | -------------------- | ---------------------------------- |
| `int tmp = counter;` |                      | `counter: 1`<br>`thread1 > tmp: 1` |
|                      | `int tmp = counter;` | `counter: 1`<br>`thread2 > tmp: 1` |
| `tmp++;`             |                      | `counter: 1`<br>`thread1 > tmp: 2` |
|                      | `tmp++;`             | `counter: 1`<br>`thread2 > tmp: 2` |
| `counter = tmp;`     |                      | `counter: 2`<br>`thread2 > tmp: 2` |
|                      | `counter = tmp;`     | `counter: 2`<br>`thread2 > tmp: 2` |

Both of these cases can happen, as threads run **asynchronously**. 