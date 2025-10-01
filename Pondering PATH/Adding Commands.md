# Pondering PATH

## Adding Commands 
Recall our example from the previous level:
```
hacker@dojo:~$ ls /home/hacker/scripts
goodscript	badscript	okayscript
hacker@dojo:~$ PATH=/home/hacker/scripts
hacker@dojo:~$ goodscript
YEAH! This is the best script!
hacker@dojo:~$
```
What we see here, of course, is the hacker making the shell more useful for themselves by bringing their own commands to the party. Over time, you might amass your own elegant tools. Let's start with win!

Previously, the win command that /challenge/run executed was stored in /challenge/more_commands. This time, win does not exist! Recall the final level of Chaining Commands, and make a shell script called win, add its location to the PATH, and enable /challenge/run to find it!

Hint: /challenge/run runs as root and will call win. Thus, win can simply cat the flag file. Again, the win command is the only thing that /challenge/run needs, so you can just overwrite PATH with that one directory. But remember, if you do that, your win command won't be able to find cat.

You have three options to avoid that:

Figure out where the cat program is on the filesystem. It must be in a directory that lives in the PATH variable, so you can print the variable out (refer to Shell Variables to remember how!), and go through the directories in it (recall that the different entries are separated by :), find which one has cat in it, and invoke cat by its absolute path.
Set a PATH that has the old directories plus a new entry for wherever you create win.
Use read (again, refer to Shell Variables) to read /flag. Since read is a builtin functionality of bash, it is unaffected by PATH shenanigans.
Now, go and win!

### Solve
**Flag:** `pwn.college{kkt23BP8DY5knPcNHT6QHSbpW3v.QX2cjM1wSNyMzNzEzW}`

When `/challenge/run` is run, it will run as root and only invoke the command `win`. Since the program is running as root, we can define `win` as a shell script which will use `cat` to read `/flag`. We can then put the directory `win` is located in into the `PATH` variable.

However, this will also remove the directory `cat` is located in from the `PATH` variable. Therefore, we should first find the address of `cat` using the `which` command, and use that path to invoke `cat` in the shell script. 

Therefore, the shell script `/home/hacker/win` should be:
```
#!/bin/bash
/run/dojo/bin/cat /flag
```
After making the shell script, it can be made executable by all users using `chmod a+x`. The `PATH` variable can now be set to `/home/hacker` (directory of `win`).

```
which cat
/run/dojo/bin/cat
chmod a+x /home/hacker/win
PATH="/home/hacker"
/challenge/run
bash: sed: command not found
Invoking 'win'....
pwn.college{kkt23BP8DY5knPcNHT6QHSbpW3v.QX2cjM1wSNyMzNzEzW}
```
### New Learnings

We can add the directories of shell scripts to the `PATH` variable, allowing us to create our own commands in the terminal.