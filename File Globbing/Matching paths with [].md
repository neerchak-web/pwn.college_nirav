# File Globbing

## Matching paths with []
Globbing happens on a path basis, so you can expand entire paths with your globbed arguments. For example:
```
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: /home/hacker/file_[ab]
Look: /home/hacker/file_a /home/hacker/file_b
```
Now it's your turn. Once more, we've placed a bunch of files in /challenge/files. Starting from your home directory, run /challenge/run with a single argument that bracket-globs into the absolute paths to the file_b, file_a, file_s, and file_h files!


### Solve
**Flag:** `pwn.college{AmdZSmDWoP-ah1lGAiZpG20X1ja.QX0IDO0wSNyMzNzEzW}`

To retrieve the flag, we need to change the current working directory to `/challenge` and run `/challenge/run` with the arguments as the absolute paths of `file_b`, `file_a`, `file_s`, and `file_h` to retrieve the flag. However, we are allowed to run `/challenge/run` with only one argument.

Each file is located in `/challenge/files`. Therefore, we can combine the absolute paths of all the files in one argument using `/challenge/files/file_[bash]`.

```
/challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{AmdZSmDWoP-ah1lGAiZpG20X1ja.QX0IDO0wSNyMzNzEzW}
```

### New Learnings

The use of `[]` is not limited to file/directory names. It can also be used to expand paths.
