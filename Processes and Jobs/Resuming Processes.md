# Processes and Jobs

## Resuming Processes 
Usually, when you suspend processes, you'll want to resume them at some point. Otherwise, why not just terminate them? To resume processes, your shell provides the fg command, a builtin that takes the suspended process, resumes it, and puts it back in the foreground of your terminal.

Go try it out! This challenge's run needs you to suspend it, then resume it. Good luck!


### Solve
**Flag:** `pwn.college{cCB4lHgJ0-vZO3ESnjD0OyqdrLS.QX1QDO0wSNyMzNzEzW}`

To retrieve the flag, we need to run `/challenge/run`, suspend (not terminate) it, and resume the suspended program. Suspended programs can be resumed using the `fg` command.

```
/challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with 
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
fg /challenge/run
/challenge/run
I'm back! Here's your flag:
pwn.college{83PubSaVdvWDL15DE0jciR9N7QD.QX2QDO0wSNyMzNzEzW}
Don't forget to press Enter to quit me!

Goodbye!
```
### New Learnings

`fg` is a command used to resume suspended programs. It takes the suspended program as its argument.

