# Processes and Jobs

## Starting Backgrounded Processes 
Of course, you don't have to suspend processes to background them: you can start them backgrounded right off the bat! It's easy; all you have to do is append a & to the command, like so:
```
hacker@dojo:~$ sleep 1337 &
[1] 1771
hacker@dojo:~$ ps -o user,pid,stat,cmd
USER         PID STAT CMD
hacker      1709 Ss   bash
hacker      1771 S    sleep 1337
hacker      1782 R+   ps -o user,pid,stat,cmd
hacker@dojo:~$ 
```
Here, sleep is actively running in the background, not suspended. Now it's your turn to practice! Launch /challenge/run backgrounded for the flag!


### Solve
**Flag:** `pwn.college{kqKeZQuL0kzW0mHbGHI1EcIOLbd.QX5QDO0wSNyMzNzEzW}`

To retrieve the flag, we need to run `/challenge/run` in the background. To run a process in the background, add a `&` symbol at the end of the command.

```
/challenge/run &
[1] 149
 


Yay, you started me in the background! Because of that, this text will probably 
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{kqKeZQuL0kzW0mHbGHI1EcIOLbd.QX5QDO0wSNyMzNzEzW}
```
### New Learnings

To run a command in the background, add a `&` symbol at the end of the command.

