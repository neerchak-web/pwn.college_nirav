# Chaining Commands

## Reading Shell Scripts
You're not the only one who writes shell scripts! They are very handy for doing simple "system-level" tasks, and are a common tool that developers and sysadmins reach for. In fact, a surprising fraction of the programs on a typical Linux machine are shell scripts.

In this level, we will learn to read shell scripts. /challenge/run is a shell script that requires you to put in a secret password, but that password is hardcoded into the script iself! Read the script (using, say, cat), figure out the password, and get the flag!
1

### Solve
**Flag:** `pwn.college{I_YDMGX6BCz_FO5H8Dlg-ro7Z8o.0lMwgDOxwSNyMzNzEzW}`

The password to shell script `/challenge/run` is in the shell script itself. We can read it using `cat` and then run the program with the correct password.

```
cat /challenge/run
#!/opt/pwn.college/bash

read GUESS
if [ "$GUESS" == "hack the PLANET" ]
then
        echo "CORRECT! Your flag:"
        cat /flag
else
        echo "Read the /challenge/run file to figure out the correct password!"
fi
hacker@chaining~reading-shell-scripts:~$ /challenge/run
hack the PLANET
CORRECT! Your flag:
pwn.college{I_YDMGX6BCz_FO5H8Dlg-ro7Z8o.0lMwgDOxwSNyMzNzEzW}
```
### New Learnings

Shell scripts' content, like other files' content, can be read using commands like `cat`.