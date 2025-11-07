

## Hard Link
- giving many **names** to the **same, existing file**
- alias to a file
- Provides a way to access the same file from many locations
- **Cannot** hard link a directory
	- prevents circular links
	- file cannot link its parent directory
- Only used within the **same file system**
- Created using command `ln [file] [hard link name]`

> [!tip] Note
> Hard links have the **same i-node** as the original file, as they are the same file.

For example, linking the file `hello.txt` to `hard_link`:
```shell
$ ln hello.txt hard_link
```

The contents of the two files are now the same:
```shell
$ cat hello.txt
Hello
$ cat hard_link
Hello
```

If we modify the content of `hello.txt`, the effect is seen on `hard_link` as well:
```shell
$ echo World >> hello.txt
$ cat hello.txt
Hello
World
$ cat hard_link
Hello
World
```

Using `rm` on the file only **unlinks** the file
- Only when there are **no more links**, the file is actually deleted
- Hard links can be used to "**back up**" data without using any disk space
	- If we `rm` the original file, the back up stays


---
## Soft Link
- a **symbolic** link to a file
- Unlike hard links, soft links are **real files**
	- The contents of soft links are the **path** to the original file
- Directories are allowed
- Do not have to be in the same file system
- Created using the `-s` flag on `ln`

For example, linking the file `hello.txt` to `hard_link`:
```shell
$ ln hello.txt soft_link
```

The listing command `ls` can show the soft link existence with `-l`
```shell
$ ls -l
-rw-r--r-- 2 cmpt201 cmpt201 12 Nov  6 22:05 hello.txt
lrwxrwxrwx 1 cmpt201 cmpt201  9 Nov  6 22:15 soft_link -> hello.txt
```

We can access the contents of `hello.txt` through both files
```shell
$ cat hello.txt
Hello
$ cat soft_link
Hello
```

However, if we remove the original file `hello.txt`, the link is broken and is not accessible
```console
$ rm hello.txt
$ cat soft_link
cat: soft_link: No such file or directory
```

The `cat` returns an error saying no such file, although the soft link file still exists
```shell
$ ls -l
lrwxrwxrwx 1 cmpt201 cmpt201  9 Nov  6 22:15 soft_link -> hello.txt
```

A **broken** soft link is like a **dangling pointer**. It points to a file that no longer exists.

