# Comprehending Commands

## comparing files
When looking for changes between similar files, eyeballing them might not be the most efficient approach! This is where the diff command becomes invaluable.

diff compares two files line by line and shows you exactly what's different between them. For example:
```
hacker@dojo:~$ cat file1
hello
world
hacker@dojo:~$ cat file2
hello
universe
hacker@dojo:~$ diff file1 file2
2c2
< world
---
> universe
```
The output tells us that line 2 changed (2c2), with world in the first file (<) being replaced by universe in the second file (>).

Sometimes, when new lines are added, you'll see something like:
```
hacker@dojo:~$ cat old
pwn
hacker@dojo:~$ cat new
pwn
college
hacker@dojo:~$ diff old new
1a2
> college
```
This tells us that after line 1 in the first file, the second file has an additional line (1a2 means "after line 1 of file1, add line 2 of file2").

Now for your challenge! There are two files in /challenge:

/challenge/decoys_only.txt contains 100 fake flags
/challenge/decoys_and_real.txt contains all 100 fake flags plus the one real flag
Use diff to find what's different between these files and get your flag!



### Solve
**Flag:** `pwn.college{YIhtadLpEWm-o9bqY7Sq10I8btF.01MwMDOxwSNyMzNzEzW}`

It is given that `/challenge/decoys_only.txt` contains 100 fake flags
and `/challenge/decoys_and_real.txt` contains all 100 fake flags plus the one real flag. 

Using `diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt`, we can get the line in the second file which is missing in the first file. This line is the required flag.

```
diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt
65a66
> pwn.college{YIhtadLpEWm-o9bqY7Sq10I8btF.01MwMDOxwSNyMzNzEzW}
```

### New Learnings

`diff` is a command used to identify the changes between two files, line by line. 

When two files with the same number of lines are given as arguments to `diff`, the lines which do not match are returned, along with their position with respect to each file.

If two files with different number of lines are given as arguments to `diff`, it returns the additional line and the position at which it occurs.

