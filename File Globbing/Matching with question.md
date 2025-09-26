# File Globbing

## Matching with ?
Next, let's learn about ?. When it encounters a ? character in any argument, the shell will treat it as a single-character wildcard. This works like *, but only matches one character. For example:
```
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_cc
hacker@dojo:~$ ls
file_a	file_b	file_cc
hacker@dojo:~$ echo Look: file_?
Look: file_a file_b
hacker@dojo:~$ echo Look: file_??
Look: file_cc
```
Now, practice this yourself! Starting from your home directory, change your directory to /challenge, but use the ? character instead of c and l in the argument to cd! Once you're there, run /challenge/run for the flag!


### Solve
**Flag:** `pwn.college{I9fk7absDbtdAatFRuH2jy3zN6N.QXyIDO0wSNyMzNzEzW}`

To retrieve the flag, we need to change the current working directory to `/challenge` and run `/challenge/run` to retrieve the flag. However, we need to use the single charcter wildcard `?` for the characters `c` and `l`.

Therefore, the command to change the directory should be `cd /?ha??enge`.

```
cd /?ha??enge
/challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{I9fk7absDbtdAatFRuH2jy3zN6N.QXyIDO0wSNyMzNzEzW}
```

### New Learnings

`?` is a wildcard character. It matches a single charcter and is expanded before the command is run. It does not match the `/` character.

For example, `ls ?.txt` will display all files in the current directory of type `.txt` whose names are exactly one character.
