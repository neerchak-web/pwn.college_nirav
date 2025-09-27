# Data Manipulation

## Deleting characters
tr can also translate characters to nothing (i.e., delete them). This is done via a -d flag and an argument of what characters to delete:
```
hacker@dojo:~$ echo PAWN | tr -d A
PWN
hacker@dojo:~$
```
Pretty simple! Now you give it a try. I'll intersperse some decoy characters (specifically: ^ and %) among the flag characters. Use tr -d to remove them!



### Solve
**Flag:** `pwn.college{wiUqSmmJHBNT6jdXRQGJQ8VeKpl.0FNxEzNxwSNyMzNzEzW}`

Running `/challenge/run` will print the flag with extra `^` and `%` characters. We can pipe the output to `tr` and filter out the additional characters using the `-d` flag.

```
/challenge/run | tr -d ^%
Your character-stuffed flag:
pwn.college{wiUqSmmJHBNT6jdXRQGJQ8VeKpl.0FNxEzNxwSNyMzNzEzW}
```
### New Learnings

`tr` command can be used with the `-d` flag to filter out characters specified in its argument from the input.