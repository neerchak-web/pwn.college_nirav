# Terminal Multiplexing

## Switching Windows
Okay, so far, screen is just a weird sort of terminal-with-a-terminal. But it can be much more!

Inside a single screen session, you can have multiple windows, like your browser has multiple tabs. This can be super handy for organizing different tasks!

These windows are handled with different keyboard shortcuts, all starting with Ctrl-A:

Ctrl-A c - Create a new window
Ctrl-A n - Next window
Ctrl-A p - Previous window
Ctrl-A 0 through Ctrl-A 9 - Jump directly to window 0-9
Ctrl-A " - bring up a selection menu of all of the windows
For this challenge, we've set up a screen session with two windows:

Window 0 has... well, you'll have to switch there to find out!
Window 1 has a welcome message
Attach to the session with screen -r, then use one of the key combinations above to switch to Window 1. Go get that flag!

### Solve
**Flag:** `pwn.college{4wPtGqaxjDMA8UVSmwVQV4FJXXb.0FO4IDOxwSNyMzNzEzW}`

To retrieve the flag, we need to reattach to the screen session loaded in. This will load us into window 1. We can use Ctrl-A 0 to go to window 0 and retrieve the flag.
```
screen -r
cat <<MSG
> Welcome to the window switching challenge!
> You are currently in window 1.
> The flag is hidden in window 0.
> Use Ctrl-A 0 to switch to window 0!
> MSG
Welcome to the window switching challenge!
You are currently in window 1.
The flag is hidden in window 0.
Use Ctrl-A 0 to switch to window 0!
cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{4wPtGqaxjDMA8UVSmwVQV4FJXXb.0FO4IDOxwSNyMzNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{4wPtGqaxjDMA8UVSmwVQV4FJXXb.0FO4IDOxwSNyMzNzEzW}
```
### New Learnings

A single screen session can have multiple windows which can be navigated and created using the following shortcuts: 

Ctrl-A c - Create a new window
Ctrl-A n - Next window
Ctrl-A p - Previous window
Ctrl-A 0 through Ctrl-A 9 - Jump directly to window 0-9
Ctrl-A " - bring up a selection menu of all of the windows
