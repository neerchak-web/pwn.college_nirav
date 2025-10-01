# Pondering PATH

## The PATH Variable
It turns out that the answer to "How does the shell find ls?" is fairly simple. There is a special shell variable, called PATH, that stores a bunch of directory paths in which the shell will search for programs corresponding to commands. If you blank out the variable, things go badly:
```
hacker@dojo:~$ ls
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
hacker@dojo:~$ PATH=""
hacker@dojo:~$ ls
bash: ls: No such file or directory
hacker@dojo:~$
```
Without a PATH, bash cannot find the ls command.

In this level, you will disrupt the operation of the /challenge/run program. This program will DELETE the flag file using the rm command. However, if it can't find the rm command, the flag will not be deleted, and the challenge will give it to you! Thus, you must make it so that /challenge/run also can't find the rm command!

Keep in mind: /challenge/run will be a child process of your shell, so you must apply the concepts you learned in Shell Variables to mess with its PATH variable! If you don't succeed, and the flag gets deleted, you will need to restart the challenge to try again!


### Solve
**Flag:** `pwn.college{MmQ-IdqhLRb6UsCGS-5XiqUOxbJ.QX2cDM1wSNyMzNzEzW}`

To retrieve the flag, we need to run `/challenge/run`. The program will delete the flag file using `rm`. Since the path to `rm` is stored in the shell variable `PATH`, blanking out the variable will stop the program from being able to find the `rm` command.

`/challenge/run` is a child process of our terminal shell, therefore the shell variable needs to be exported using `export` after blanking it out.

After doing so, the program will instead display the required flag.

```
export PATH=""
/challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{MmQ-IdqhLRb6UsCGS-5XiqUOxbJ.QX2cDM1wSNyMzNzEzW}
```
### New Learnings

`PATH` is a shell variable which stores certain directory paths in it. When a command is invoked in the shell, the shell looks for programs in the directories listed in `PATH` which correspond to the command.

The `PATH` variable's contents can also be modified or reset, which will affect the shell's ability to run certain commands.