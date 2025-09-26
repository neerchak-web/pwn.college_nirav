# File Globbing

## Matching with *
The first glob we'll learn is *. When it encounters a * character in any argument, the shell will treat it as a "wildcard" and try to replace that argument with any files that match the pattern. It's easier to show you than explain:
```
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: file_*
Look: file_a file_b file_c
```
Of course, though in this case, the glob resulted in multiple arguments, it can just as simply match only one. For example:
```
hacker@dojo:~$ touch file_a
hacker@dojo:~$ ls
file_a
hacker@dojo:~$ echo Look: file_*
Look: file_a
```
When zero files are matched, by default, the shell leaves the glob unchanged:
```
hacker@dojo:~$ touch file_a
hacker@dojo:~$ ls
file_a
hacker@dojo:~$ echo Look: nope_*
Look: nope_*
```
The * matches any part of the filename except for / or a leading . character. For example:
```
hacker@dojo:~$ echo ONE: /ho*/*ck*
ONE: /home/hacker
hacker@dojo:~$ echo TWO: /*/hacker
TWO: /home/hacker
hacker@dojo:~$ echo THREE: ../*
THREE: ../hacker
```
Now, practice this yourself! Starting from your home directory, change your directory to /challenge, but use globbing to keep the argument you pass to cd to at most four characters! Once you're there, run /challenge/run for the flag!


### Solve
**Flag:** `pwn.college{MLGPS_OKM2crk0Do-UhZnYEseZs.QXxIDO0wSNyMzNzEzW}`

To retrieve the flag, we need to change the current working directory to `/challenge` and run `/challenge/run` to retrieve the flag. However, we are only allowed pass an argument of atmost four characters to cd.

We can take the first three characters from `/challenge`, and use `*`. This will change the directory to a directory whose name begins with `/ch`, if exactly one such directory exists.

```
cd /ch*
/challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{MLGPS_OKM2crk0Do-UhZnYEseZs.QXxIDO0wSNyMzNzEzW}
```

### New Learnings

`*` is a wildcard character. It matches any string of charcters and is expanded before the command is run. It does not match the `/` character.

For example, `ls *.txt` will display all files in the current directory that end with the pattern `.txt`.
