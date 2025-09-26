# File Globbing

## Matching with []
Next, we will cover []. The square brackets are, essentially, a limited form of ?, in that instead of matching any character, [] is a wildcard for some subset of potential characters, specified within the brackets. For example, [pwn] will match the character p, w, or n. For example:
```
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: file_[ab]
Look: file_a file_b
```
Try it here! We've placed a bunch of files in /challenge/files. Change your working directory to /challenge/files and run /challenge/run with a single argument that bracket-globs into file_b, file_a, file_s, and file_h!


### Solve
**Flag:** `pwn.college{8r5p6YSQaDDtht4iELRTsuOgAUm.QXzIDO0wSNyMzNzEzW}`

To retrieve the flag, we need to change the current working directory to `/challenge` and run `/challenge/run` with the arguments `file_b`, `file_a`, `file_s`, and `file_h` to retrieve the flag. However, we are allowed to run `/challenge/run` with only one argument.

We can combine the four files in one argument using the `[]` wildcard.

```
cd /challenge/files
/challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{8r5p6YSQaDDtht4iELRTsuOgAUm.QXzIDO0wSNyMzNzEzW}
```

### New Learnings

`[]` is a wildcard character. Unlike `?` which matches a single character with every character, `[]` matches a single character with only the characters specified inside the brackets.

For example, `ls [abc].txt` will display all files in the current directory of type `.txt` whose names are either the character `a`, `b` or `c`.
