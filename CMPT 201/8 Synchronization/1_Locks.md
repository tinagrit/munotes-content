
> [!fail] This note is incomplete.

## Synchronization
- When having multiple threads, execution needs to be **synchronized** and coordinated
- Avoids **race cases**, as they can be very difficult to debug
	- Race cases are rare
	- Debugging requires attention to multiple threads at the same time


---
## Mutex
- One operation, like `counter++` mentioned in [[2_Data Race|Data Race]], can be a **number of operations** within it. 
- MUTEX, stands for **Mutual Exclusion** prevents the mix up of sub operations

### Defining the lock


### Grabbing the lock


### Releasing the lock
