

## Virtual File System
- **interface** that different file systems can implement
	- includes: open, read, write, close, etc.
- not a real file
	- software **pretending** to be a file system
	- can be used as Linux file system
	- e.g. [[2_UNIX Files#/proc|/proc]], [[2_UNIX Files#/dev|/dev]]

### Mounting
- In Windows, each root `/` is **different for each** file system
	- running `cd /` will take the user to `C:` or `D:` or any partition that they are currently on
- In Linux, all file systems are in **a single tree**, starting at root `/`
	- multiple trees combined together

**Mounting** refers to combining multiple trees
- **All file systems** are formed into a single tree, like what Linux works on
- Command `mount` mounts a file system to a directory
- To show information on mounting, use the command `mount` or access `/proc/mounts`
