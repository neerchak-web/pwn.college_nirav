# Terminal Multiplexing

## Deattaching and Attaching (tmux)
Let's try the same thing with tmux!

tmux (terminal multiplexer) is screen's younger, more modern cousin. It does all the same things but with some different key bindings. The biggest difference? Instead of Ctrl-A, tmux uses Ctrl-B as its command prefix.

So to detach from tmux, you press Ctrl-B followed by d.
```
hacker@dojo:~$ tmux
[doing some work...]
[Press Ctrl-B, then d]
[detached (from session 0)]
hacker@dojo:~$ 
```
The commands also differ:
```
tmux ls - List sessions
tmux attach or tmux a - Reattach to session
```
For this challenge:

Launch tmux
Detach from it.
Run /challenge/run (this will send the flag to your detached session!)
Reattach to see your prize

### Solve
**Flag:** `pwn.college{4wPtGqaxjDMA8UVSmwVQV4FJXXb.0FO4IDOxwSNyMzNzEzW}`

To retrieve the flag, we need launch `tmux`, detach from it using `ctrl-B` followed by `d`, run `/challenge/run` and retach to the detached screen using `tmux a`.
```
tmux
[detached (from session 0)]
/challenge/run
Found detached tmux session: 0
Sending flag to your tmux session...

Flag sent! Now reattach to your tmux session with:
  tmux attach

You'll find the flag waiting for you there!
tmux attach
echo Congratulations, here is your flag: pwn.college{IV2Vgv_oPJEK68ZHN5fVN8ystVo.0VO4IDOxwSNyMzNzEzW}
Congratulations, here is your flag: pwn.college{IV2Vgv_oPJEK68ZHN5fVN8ystVo.0VO4IDOxwSNyMzNzEzW}
[detached (from session 0)]
```
### New Learnings

Screen sessions can also be created using `tmux` command, with different keybinds from `screen` command.