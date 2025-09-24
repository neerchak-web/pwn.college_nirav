# Comprehending Commands

## touching files
Of course, you can also create files! There are several ways to do this, but we'll look at a simple command here. You can create a new, blank file by touching it with the touch command:
```
hacker@dojo:~$ cd /tmp
hacker@dojo:/tmp$ ls
hacker@dojo:/tmp$ touch pwnfile
hacker@dojo:/tmp$ ls
pwnfile
hacker@dojo:/tmp$
```
It's that simple! In this level, please create two files: /tmp/pwn and /tmp/college, and run /challenge/run to get your flag!




### Solve
**Flag:** `pwn.college{4a_hCbNvUqnB0d0SgbKb-cR2ag7.QXwMDO0wSNyMzNzEzW}`

The challenge requires us to create two files `pwn` and `college` in the `/temp` directory. We can change the current working directory to `/temp` using `cd` command.

Once in `/temp`, we can use the `touch` command to create the required files, one by one. After creating the files, we can execute `/challenge/run` to retrieve the flag.

```
cd /tmp
touch pwn
touch college
/challenge/run
Success! Here is your flag:
pwn.college{4a_hCbNvUqnB0d0SgbKb-cR2ag7.QXwMDO0wSNyMzNzEzW}
```

### New Learnings

`touch` is a command that creates an empty file named as its argument in the current working directory, if the file does not already exist.

