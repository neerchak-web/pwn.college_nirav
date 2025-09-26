# Practicing Piping

## Redirecting output
First, let's look at redirecting stdout to files. You can accomplish this with the > character, as so:
```
hacker@dojo:~$ echo hi > asdf
```
This will redirect the output of echo hi (which will be hi) to the file asdf. You can then use a program such as cat to output this file:
```
hacker@dojo:~$ cat asdf
hi
```
In this challenge, you must use this output redirection to write the word PWN (all uppercase) to the filename COLLEGE (all uppercase).


### Solve
**Flag:** `pwn.college{EpVNtQOnhdhVi-HbIvQG_C6BCcW.QX0YTN0wSNyMzNzEzW}`

To retrieve the flag, we need to write the pattern "PWN" into a file named `COLLEGE`. We can use `> COLLEGE` to write the output of a program (specified before the command) into the file `COLLEGE`.

The `echo` command can take a pattern as its argument and print the pattern back as its output. Therefore, we can use `echo PWN` as the program whose output must be redirected into the file `COLLEGE`.
```
echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your 
flag:
pwn.college{EpVNtQOnhdhVi-HbIvQG_C6BCcW.QX0YTN0wSNyMzNzEzW}
```

### New Learnings

The `>` character is used to redirect the output of a program specified before it into a file specified after it.