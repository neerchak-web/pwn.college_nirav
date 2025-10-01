# Pondering PATH

## Setting PATH 
Okay, so things break when you blank out PATH. But what about doing something useful with PATH?

Let's explore how we would, for example, add a new directory of programs to our command repertoire. Recall that PATH stores a list of directories to find commands in and, for commands in nonstandard places, we must typically execute them via their path:
```
hacker@dojo:~$ ls /home/hacker/scripts
goodscript	badscript	okayscript
hacker@dojo:~$ goodscript
bash: goodscript: command not found
hacker@dojo:~$ /home/hacker/scripts/goodscript
YEAH! This is the best script!
hacker@dojo:~$
```
If you maintain useful scripts that you want to be able to launch by bare name, this is annoying. However, by adding directories to or replacing directories in this list, you can expose these programs to be launched using their bare name! For example:
```
hacker@dojo:~$ PATH=/home/hacker/scripts
hacker@dojo:~$ goodscript
YEAH! This is the best script!
hacker@dojo:~$
```
Let's practice. This level's /challenge/run will run the win command via its bare name, but this command exists in the /challenge/more_commands/ directory, which is not initially in the PATH. The win command is the only thing that /challenge/run needs, so you can just overwrite PATH with that one directory. Good luck!

### Solve
**Flag:** `pwn.college{sadNh6urkXQyrBTO8A3heQEVwkM.QX1cjM1wSNyMzNzEzW}`

To retrieve the flag, we need to run `/challenge/run`. The program will run the command `win`. However the program named `win` is in the directory `/challenge/more_commands`, and this directory is not in `PATH`.

To make sure `/challenge/run` can run the command `win` without it's path, we can set `PATH` to only store the `/challenge/more_commands` directory in it.

```
PATH=/challenge/more_commands
/challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{sadNh6urkXQyrBTO8A3heQEVwkM.QX1cjM1wSNyMzNzEzW}
```
### New Learnings

We can set or add our own directories in the `PATH` variable. This will allow us to run programs in those directories as commands using only their names.