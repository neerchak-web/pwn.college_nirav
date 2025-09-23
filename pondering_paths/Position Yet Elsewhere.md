# Pondering Paths

## Position Yet Elsewhere
The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the cd (change directory) command and passing a path to it as an argument, as so:
```
hacker@dojo:~$ cd /some/new/directory
hacker@dojo:/some/new/directory$
```
This affects the "current working directory" of your process (in this case, the bash shell). Each process has a directory in which it's currently hanging out. The reasons for this will become clear later in the module.

As an aside, now you can see what the ~ was in the prompt! It shows the current path that your shell is located at.

This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you). You'll need to cd to that directory before rerunning the challenge program. Good luck!



### Solve
**Flag:** `pwn.college{cpW3zNSQtyo7-UUDRDsF_ZrbmD8.QX4QTN0wSNyMzNzEzW}`

As before, `run` needs to be executed from a specific path. Attempting to execute it from `challenge` directory will display the absolute path of the directory `run` is located in. The absolute path of `run` can be used to execute it and retrieve the flag.

```
/challenge/run
Incorrect...
You are not currently in the /usr/bin directory.
Please use the `cd` utility to change directory appropriately.
cd /usr/bin
/challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{cpW3zNSQtyo7-UUDRDsF_ZrbmD8.QX4QTN0wSNyMzNzEzW}
```

### New Learnings
In this challenge, we used `cd` to navigate through multiple levels of subdirectories in a single command, allowing us to change the current working directory to the directory `run` is located in.
