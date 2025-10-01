# Pondering PATH

## Finding Commands 
When you type the name of a command, something inside one of the many directories listed in your $PATH variable is what actually gets executed (of course, unless the command is a builtin!). But which file, precisely? You can find out with the aptly-named which command:
```
hacker@dojo:~$ which cat
/bin/cat
hacker@dojo:~$ /bin/cat /flag
YEAH
hacker@dojo:~$
```
Mirroring what the shell does when searching for commands, which looks at each directory in $PATH in order and prints the first file it finds whose name matches the argument you passed.

In this challenge, we added a win command somewhere in your $PATH, but it won't give you the flag. Instead, it's in the same directory as a flag file that we made readable by you! You must find win (with the which command), and cat the flag out of that directory!

### Solve
**Flag:** `pwn.college{AjicuDWc0lvFMW3Ar8_jsMXXVmz.01NzEzNxwSNyMzNzEzW}`

To retrieve the flag, we need to find the `flag` file. It is located in the same directory as the `win` command which is located in one of the `PATH` directories. We can use `which` command to search the `PATH` directories for `win`.

Once we find the right directory in `PATH`, we can `cd` to it and read the `flag` file using `cat`.

```
which win
/challenge/paths/12849/win
cd /challenge/paths/12849
cat flag
pwn.college{AjicuDWc0lvFMW3Ar8_jsMXXVmz.01NzEzNxwSNyMzNzEzW}
```
### New Learnings

The `which` command is used to search all the directories in `PATH` for the command given as its argument. It behaves similarly to how shell does when it looks for a command in the `PATH` directories.

`which` will print the first matching file it finds.