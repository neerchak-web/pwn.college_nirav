# File Globbing

## Exclusionary globbing
Sometimes, you want to filter out files in a glob! Luckily, [] helps you do just this. If the first character in the brackets is a ! or (in newer versions of bash) a ^, the glob inverts, and that bracket instance matches characters that aren't listed. For example:
```
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: file_[!ab]
Look: file_c
hacker@dojo:~$ echo Look: file_[^ab]
Look: file_c
hacker@dojo:~$ echo Look: file_[ab]
Look: file_a file_b
```
Armed with this knowledge, go forth to /challenge/files and run /challenge/run with all files that don't start with p, w, or n!

NOTE: The ! character has a different special meaning in bash when it's not the first character of a [] glob, so keep that in mind if things stop making sense! ^ does not have this problem, but is also not compatible with older shells.



### Solve
**Flag:** `pwn.college{wqhuovb5sRrfyi8B6qCZneR7nvL.QX2IDO0wSNyMzNzEzW}`

To retrieve the flag, we need to change the current working directory to `/challenge/files` and run `/challenge/run` with all files that don't start with `p`, `w`, or `n`.

We can do so using the argument `[!pwn]*`. `[!pwn]` will filter out all files which don't start with any of the characters enclosed inside `[]`. The `*` glob will match all remaining characters.

```
cd /challenge/files
/challenge/run [!pwn]*
You got it! Here is your flag!
pwn.college{wqhuovb5sRrfyi8B6qCZneR7nvL.QX2IDO0wSNyMzNzEzW}
```

### New Learnings

The `[]` can also be used to filter out characters instead of matching characters by making the first character inside the brackets as `!`. `[]` will filter out all characters inside after `!`.
