# Terminal Multiplexing

## Launching Screen
Let's dive right in!

screen is a program that creates virtual terminals inside your terminal. It's somewhat like having multiple browser tabs, but for your command line!

Starting screen is super simple:
```
hacker@dojo:~$ screen
```
That's it! You're now inside a screen session. It looks exactly like a terminal, but there are new capabilities there, waiting to be discovered.

For this challenge, we've hooked things up so that just launching screen will get you the flag. Easy!

### Solve
**Flag:** `pwn.college{Udi9Zm7b81J_A3k2vBIeMdCyUrG.0VN4IDOxwSNyMzNzEzW}`

To retrieve the flag, we need to launch a screen session and exit. This can be done using the `screen` command. Enter "exit" to return to the original terminal session.

```
screen
Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{Udi9Zm7b81J_A3k2vBIeMdCyUrG.0VN4IDOxwSNyMzNzEzW}
```
### New Learnings

`screen` is a command which creates virtual terminal windows inside the current terminal session.