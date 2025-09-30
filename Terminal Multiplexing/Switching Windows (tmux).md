# Terminal Multiplexing

## Switching Windows (tmux)
Let's learn to navigate windows in tmux!

Just like screen, tmux has windows. The key combos are different, but the concept is the same:
```
Ctrl-B c - Create a new window
Ctrl-B n - Next window
Ctrl-B p - Previous window
Ctrl-B 0 through Ctrl-B 9 - Jump to window 0-9
Ctrl-B w - See a nice window picker
```
Tmux shows your windows at the bottom in a status bar that looks like:
```
[0] 0:bash* 1:bash
```
The * shows your current window, and each entry also shows the process that the window was created to run.

We've created a tmux session with two windows:

Window 0 has the flag!
Window 1 has your warm welcome.
Go get that flag!


### Solve
**Flag:** `pwn.college{wMfvlwvwcyKdwmcHzLL0AfJbY_F.0FM5IDOxwSNyMzNzEzW}`

To retrieve the flag, we need reattach the tmux session loaded in. This will take us to window 1. To get to the flag in window 0, we can use `ctrl-B` and enter 0.
```
tmux a
cat <<MSG
Welcome to the tmux window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-B 0 to switch to window 0!
MSG
cat <<MSG
> Welcome to the tmux window switching challenge!
> You are currently in window 1.
> The flag is hidden in window 0.
> Use Ctrl-B 0 to switch to window 0!
> MSG
Welcome to the tmux window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-B 0 to switch to window 0!
cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{wMfvlwvwcyKdwmcHzLL0AfJbY_F.0FM5IDOxwSNyMzNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{wMfvlwvwcyKdwmcHzLL0AfJbY_F.0FM5IDOxwSNyMzNzEzW}
```
### New Learnings

Screen sessions can also be created using `tmux` command, with different keybinds from `screen` command.