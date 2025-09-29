# Processes and Jobs

## Foregrounding Processes 
Imagine that you have a backgrounded process, and you want to mess with it some more. What do you do? Well, you can foreground a backgrounded process with fg just like you foreground a suspended process! This level will walk you through that!

### Solve
**Flag:** `pwn.college{U3uwuYb08aiDEyN228JkzkANZ5-.QX4QDO0wSNyMzNzEzW}`

To retrieve the flag, we need to run `/challenge/run`, suspend (not terminate) it, resume it in the background, and then foreground it.

```
/challenge/run
To pass this level, you need to suspend me, resume the suspended process in the 
background, and *then* foreground it without re-suspending it! You can 
background me with Ctrl-Z (and resume me in the background with 'bg') or, if 
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
bg /challenge/run
[1]+ /challenge/run &
 


Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out. After that, resume me into the foreground with 'fg'; 
I'll wait.
fg /challenge/run
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{U3uwuYb08aiDEyN228JkzkANZ5-.QX4QDO0wSNyMzNzEzW}
```
### New Learnings

`fg` can also be used to foreground processes running in the background.

