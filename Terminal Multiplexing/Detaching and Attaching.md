# Terminal Multiplexing

## Detaching and Attaching
Now we'll start digging in with the magic of detaching!

Imagine you're working on something important over a remote connection, and your connection drops. With a normal terminal (outside of this awesome dojo environment), everything's gone. With screen, your work keeps running, and you can reattach later!

You can also detach on purpose, which we'll do in this challenge. You detach by pressing Ctrl-A, followed by d (for detach). This leaves your session running in the background while you return to your normal terminal.
```
hacker@dojo:~$ screen
[doing some work...]
[Press Ctrl-A, then d]
[detached from 12345.pts-0.hostname]
hacker@dojo:~$ 
```
To reattach, you can use the -r argument to screen:
```
hacker@dojo:~$ screen -r
```
For this challenge, you'll need to:

Launch screen
Detach from it.
Run /challenge/run (this will secretly send the flag to your detached session!)
Reattach to see your prize

### Solve
**Flag:** `pwn.college{MfCIEbhb5ErYc6RfckkLxKwOwnu.0lN4IDOxwSNyMzNzEzW}`

To retrieve the flag, we need to launch a screen session and detach from it. After running `/challenge/run`, the flag will be sent to the detached session, which can be reattached using `screen -r`.

```
screen
[detached from 147.pts-0.terminal-multiplexing~detaching-and-attaching]
/challenge/run
Found detached screen session: 147.pts-0.terminal-multiplexing~detaching-and-attaching
Sending flag to your screen session...

Flag sent! Now reattach to your screen session with:

  screen -r

You'll find the flag waiting for you there!
screen -r
[screen is terminating]
echo Yes! Flag is: pwn.college{MfCIEbhb5ErYc6RfckkLxKwOwnu.0lN4IDOxwSNyMzNzEzW}
Yes! Flag is: pwn.college{MfCIEbhb5ErYc6RfckkLxKwOwnu.0lN4IDOxwSNyMzNzEzW}
```
### New Learnings

To detach from a screen session, use the hotkey `ctrl+A` and then enter `d`. To reattach detached sessions, run `screen -r`.