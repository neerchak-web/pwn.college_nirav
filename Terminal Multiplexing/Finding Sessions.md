# Terminal Multiplexing

## Finding Sessions
Time for some screen detective work!

If you become an avid screen user, you will inevitably end up with multiple sessions running. How do you find the right one to reattach to?

Well, we can list them:
```
hacker@dojo:~$ screen -ls
There are screens on:
        23847.mysession   (Detached)
        23851.goodwork    (Detached)
        23855.morework    (Detached)
3 Sockets in /run/screen/S-hacker.
```
The identifiers of the sessions are the PID of each respective screen process, a dot, and the name of the screen session. To attach to a specific one, you use its name or its PID by giving it as an argument to screen -r.
```
hacker@dojo:~$ screen -r goodwork
```
In this challenge, we've created three screen sessions for you. One of them contains the flag. The other two are decoys!

You'll need to check each one until you find it. Don't forget to detach (Ctrl-A d) before trying the next session!

### Solve
**Flag:** `pwn.college{IeKuul5MbJ5r8wFp_zqgTSd41Mw.01N4IDOxwSNyMzNzEzW}`

To retrieve the flag, we need to find the right detcahed screen session by reattaching them one at a time using `screen -r` with their `PID`. To get the `PID`s of all running screen sessions, use `ls screen`.
```
screen -ls
There are screens on:
        264.pts-0.terminal-multiplexing~launching-screen        (Remote or dead)
        144.session_b2db5117401e678e    (Detached)
        147.session_0fdb9de8ad841185    (Detached)
        150.session_dc546988d8cc2f83    (Detached)
4 Sockets in /home/hacker/.screen.
screen -r 144
[detached from 144.session_b2db5117401e678e]
echo 'Nothing here! Try another session.'
Nothing here! Try another session.
screen -r 147
echo 'Congratulations! You found the right session!'
Congratulations! You found the right session!
echo pwn.college{IeKuul5MbJ5r8wFp_zqgTSd41Mw.01N4IDOxwSNyMzNzEzW}
pwn.college{IeKuul5MbJ5r8wFp_zqgTSd41Mw.01N4IDOxwSNyMzNzEzW}
```
### New Learnings

To reattach specific detached sessions, run `screen -r` and pass the screen session's `PID` or name as argument. To find the right argument, use `ls sleep` to dislay all screen sessions and their details.