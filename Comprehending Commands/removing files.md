# Comprehending Commands

## removing files
Files are all around you. Like candy wrappers, there'll eventually be too many of them. In this level, we'll learn to clean up!

In Linux, you remove files with the rm command, as so:
```
hacker@dojo:~$ touch PWN
hacker@dojo:~$ touch COLLEGE
hacker@dojo:~$ ls
COLLEGE     PWN
hacker@dojo:~$ rm PWN
hacker@dojo:~$ ls
COLLEGE
hacker@dojo:~$
```
Let's practice. This challenge will create a delete_me file in your home directory! Delete it, then run /challenge/check, which will make sure you've deleted it and then give you the flag!


### Solve
**Flag:** `pwn.college{owvoSE7jhPo897uC897DFwV_1NH.QX2kDM1wSNyMzNzEzW}`

The challenge requires us to delete the `delete_me` file located in our home directory and then run `/challenge/check` to retrieve the flag. To delete the required file, we can use the `rm` command.

```
rm delete_me
/challenge/check
Excellent removal. Here is your reward:
pwn.college{owvoSE7jhPo897uC897DFwV_1NH.QX2kDM1wSNyMzNzEzW}
```

### New Learnings

`rm` is a command used to delete files. It takes the file path of the file to be deleted as its argument.

