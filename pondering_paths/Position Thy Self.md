# Pondering Paths

## Position Thy Self
The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the cd (change directory) command and passing a path to it as an argument, as so:
```
hacker@dojo:~$ cd /some/new/directory
hacker@dojo:/some/new/directory$
```
This affects the "current working directory" of your process (in this case, the bash shell). Each process has a directory in which it's currently hanging out. The reasons for this will become clear later in the module.

As an aside, now you can see what the ~ was in the prompt! It shows the current path that your shell is located at.

This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you). You'll need to cd to that directory before rerunning the challenge program. Good luck!



### Solve
**Flag:** `pwn.college{EV6pJizuxmMTUuxzG8Ahp8MFQD5.QX2QTN0wSNyMzNzEzW}`

This challenge requires us to execute the program `run` like last time. However, this time the `challenge` directory is not directly located in the root directory. 

The terminal tells us the directory in which `challenge` is located. Using the `cd` (change directory) command, we can navigate to the directory in which `challenge` is located and execute `run`.

```bash
/challenge/run
Incorrect...
You are not currently in the /sys directory.
Please use the `cd` utility to change directory appropriately.
cd /sys
/challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{EV6pJizuxmMTUuxzG8Ahp8MFQD5.QX2QTN0wSNyMzNzEzW}
```

### New Learnings
`cd` (change directory) is a Linux command used to change the current working directory of the terminal session. 

The current working directory of a terminal session determines the location from which files are accessed by default.
