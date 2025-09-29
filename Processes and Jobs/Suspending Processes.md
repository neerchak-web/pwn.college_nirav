# Processes and Jobs

## Suspending Processes 
You have learned to interrupt processes with Ctrl-C, but there are less drastic measures you can use to get your terminal back! You can suspend processes to the background with Ctrl-Z. In this level, we'll explore how this works and, in the next level, we'll figure out how to resume those suspended processes!

This level's run wants to see another copy of itself running and using the same terminal. How? Use the terminal to launch it, then suspend it, then launch another copy while the first is suspended!


### Solve
**Flag:** `pwn.college{cCB4lHgJ0-vZO3ESnjD0OyqdrLS.QX1QDO0wSNyMzNzEzW}`

To retrieve the flag, we need to run `/challenge/run`, suspend (not terminate) it, and again run it. We can suspend processes using `ctrl-Z`.

```
/challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         347     337  0 17:14 pts/0    00:00:00 bash /challenge/run
root         349     347  0 17:14 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can 
background me with Ctrl-Z or, if you're not ready to do that for whatever 
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
/challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         347     337  0 17:14 pts/0    00:00:00 bash /challenge/run
root         354     337  0 17:14 pts/0    00:00:00 bash /challenge/run
root         356     354  0 17:14 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{cCB4lHgJ0-vZO3ESnjD0OyqdrLS.QX1QDO0wSNyMzNzEzW}
```
### New Learnings

`ctrl-Z` is a hotkey used to suspend processes. The suspended process will still be in the background of the shell, and can be restarted at a later time. Listing all processes using `ps` will also show suspended processes.

