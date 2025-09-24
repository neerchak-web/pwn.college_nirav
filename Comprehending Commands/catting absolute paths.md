# Comprehending Commands

## catting absolute paths
In the last level, you did cat flag to read the flag out of your home directory! You can, of course, specify cat's arguments as absolute paths:
```
hacker@dojo:~$ cat /challenge/DESCRIPTION.md

In the last level, you did `cat flag` to read the flag out of your home directory!
You can, of course, specify `cat`'s arguments as absolute paths:
...
```
In this directory, I will not copy it to your home directory, but I will make it readable. You can read it with cat at its absolute path: /flag.

FUN FACT: /flag is where the flag always lives in pwn.college, but unlike in this challenge, you typically can't access that file directly.



### Solve
**Flag:** `pwn.college{suQoKlHySr2TBBo7XbVTOQij0z4.QX5ETO0wSNyMzNzEzW}`

The problem states that the flag is stored in a file whose absolute path is `/flag`. Since the `cat` command also takes absolute paths as arguments, we can use it to retrieve the flag.

```
cat /flag
pwn.college{suQoKlHySr2TBBo7XbVTOQij0z4.QX5ETO0wSNyMzNzEzW}
```

### New Learnings
The `cat` command accepts both relative and absolute paths as arguments without change in functionality.

