# Practicing Piping

## Grepping live output
It turns out that you can "cut out the middleman" and avoid the need to store results to a file, like you did in the last level. You can do this by using the | (pipe) operator. Standard output from the command to the left of the pipe will be connected to (piped into) the standard input of the command to the right of the pipe. For example:
```
hacker@dojo:~$ echo no-no | grep yes
hacker@dojo:~$ echo yes-yes | grep yes
yes-yes
hacker@dojo:~$ echo yes-yes | grep no
hacker@dojo:~$ echo no-no | grep no
no-no
```
Now try it for yourself! /challenge/run will output a hundred thousand lines of text, including the flag. grep for the flag!

### Solve
**Flag:** `pwn.college{E9ng5yVZKRrSIFk74Qodo_BcVE4.QX5EDO0wSNyMzNzEzW}`

Running the program `/challenge/run` gives us the required flag. However, it will be hidden in a hundred thousand lines of text. Since the flag always starts with the pattern "pwn.college{", we can use `grep` to search for that pattern in the output. 

To feed the output of `/challenge/run` into `grep`, we use the `|` (pipe) operator.

```
/challenge/run | grep pwn.college{
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{E9ng5yVZKRrSIFk74Qodo_BcVE4.QX5EDO0wSNyMzNzEzW}
```

### New Learnings

The `|` operator is used to feed the output of the program specified before it into the input of the program specified after it.

This eliminates the need of redirecting the output of a program into a file and taking input for another program from the same file.