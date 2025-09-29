# Processes and Jobs

## Interrupting Processes 
You've learned how to kill other processes with the kill command, but sometimes you just want to get rid of the process that's clogging up your terminal! Luckily, terminals have a hotkey for this: Ctrl-C (e.g., holding down the Ctrl key and pressing C) sends an "interrupt" to whatever application is waiting on input from the terminal and, typically, this causes the application to cleanly exit.

Try it here! /challenge/run will refuse to give you the flag until you interrupt it. Good luck!

### Solve
**Flag:** `pwn.college{0l4Lk3yoy6cN2bPUGvWRXj3xIMt.QXzQDO0wSNyMzNzEzW}`

To retrieve the flag, we need to run `/challenge/run`. However, `/challenge/run` will not stop running on its own. To manually exit the program, we can use `ctrl-C` to return to the prompt.

```
/challenge/run
I could give you the flag... but I won't, until this process exits. Remember, 
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{0l4Lk3yoy6cN2bPUGvWRXj3xIMt.QXzQDO0wSNyMzNzEzW}
```
### New Learnings

The `ctrl-C` hotkey is used to exit from a process waiting for input from the terminal and return to the prompt.


