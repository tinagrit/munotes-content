

## Swapping
- As mentioned in [[1_Virtual Memory#Locality|Locality]], when we are out of **physical memory** we can demand **swapping**
	- Paging leverages **spatial locality**
	- Swapping only bring in pages that are in use
	- The **Page Replacement** algorithm decides which page to swap out
- **Page Fault** refers to accessing a virtual page that currently doesn't have a corresponding page frame (*it has been swapped out*)

The **optimal** algorithm will swap out the page that will not be used **for the longest time**, but this requires approximation.

Some examples of the Page Replacement algorithm include:
1. [[#First In First Out (FIFO)|First In First Out (FIFO)]]
2. [[#Least Recently Used (LRU)|Least Recently Used (LRU)]]
3. [[#Second Change|Second Chance]]


### First In First Out (FIFO)
- keeps track of when a page was **brought into memory**
- **First** one that was brought in gets **swapped out first**

### Least Recently Used (LRU)
- keeps track of when a page was **last accessed**
- The page that has **not** been used **for the longest time** gets swapped out first

### Second Change
- is an **approximation** of LRU
- Keeping track of when a page was last accessed is difficult in a larger scale
- Each page has a reference bit for identification
	- `0` initially and changed to `1` whenever it is accessed
- When there is a page fault:
	- A '**victim**' is picked. Check the reference bit for the victim.
	- A page with `0` means it **hasn't been accessed** for a while. If we need one to swap out, we can choose this page.
	- A page with `1` gets a *second chance*. The value will be replaced with `0` and the victim pointer is moved to the next page. Repeat until a `0` victim is found.


---
## Thrashing
- If a process needs a **large amount of memory**, the OS needs to **keep bringing in** new pages into the physical memory. 
- The process can be too busy trying to swap and program can be **left unexecuted**.