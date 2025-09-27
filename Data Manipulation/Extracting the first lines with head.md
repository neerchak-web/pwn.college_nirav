# Data Manipulation

## Extracting the first lines with head
In your Linux journey, you'll experience situations where you need to grab just the early output of very verbose programs. For this, you'll reach for head! The head command is used to display the first few lines of its input:
```
hacker@dojo:~$ cat /something/very/long | head
this
is
just
the
first
ten
lines
of
the
file
hacker@dojo:~$
```
By default, it shows the first 10 lines, but you can control this with the -n option:
```
hacker@dojo:~$ cat /something/very/long | head -n 2
this
is
hacker@dojo:~$
```
This challenge's /challenge/pwn outputs a bunch of data, and you'll need to pipe it through head to grab just the first 7 lines and then pipe them onwards to /challenge/college, which will give you the flag if you do this right! Your solution will be a long composite command with two pipes connecting three commands. Good luck!

### Solve
**Flag:** `pwn.college{4ohgk1t9Xo2ly_zVawtSsyexNag.0lNxEzNxwSNyMzNzEzW}`

To retrieve the flag, we need to give the first 7 lines of the output of `/challange/pwn` as input to `/challenge/college`. 

We can pipe the output of `/challange/pwn` to `head` with the `-n` flag, and argument as 7. The output of this process will be the first 7 lines of the output of `/challenge/pwn`.

This output can be piped into `/challenge/college` to retrieve the flag.

```
/challenge/pwn | head -n 7 | /challenge/college
Congratulations, you piped the right codes!
pwn.college{4ohgk1t9Xo2ly_zVawtSsyexNag.0lNxEzNxwSNyMzNzEzW}
```
### New Learnings

`head` is a command which takes input from stdin and display the first 10 lines of the input.

To specify the number of lines to be displayed, `head` can be used with the `-n` flag, which takes number of lines to be displayed as its argument.