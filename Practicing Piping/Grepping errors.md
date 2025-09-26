# Practicing Piping

## Grepping errors
You know how to redirect errors to a file, and you know how to pipe output to another program, such as grep. But what if you wanted to grep through errors directly?

The > operator redirects a given file descriptor to a file, and you've used 2> to redirect fd 2, which is standard error. The | operator redirects only standard output to another program, and there is no 2| form of the operator! It can only redirect standard output (file descriptor 1).

Luckily, where there's a shell, there's a way!

The shell has a >& operator, which redirects a file descriptor to another file descriptor. This means that we can have a two-step process to grep through errors: first, we redirect standard error to standard output (2>& 1) and then pipe the now-combined stderr and stdout as normal (|)!

Try it now! Like the last level, this level will overwhelm you with output, but this time on standard error. grep through it to find the flag!

### Solve
**Flag:** `pwn.college{09SG2dTErIJJslpQ8SX1mkkXEWK.QX1ATO0wSNyMzNzEzW}`

Running the program `/challenge/run` gives us the required flag. However, it will be hidden in lines of text in the standard error channel (`FD2`) instead of the standard output channel (`FD1`). 

If we want to redirect the output of standard error channel to wherever standard output is going, we can use `2>&1`. We can now give the combined `stderr` and `stdout` as input (`FD0`) to `grep`.

Since the flag always starts with the pattern "pwn.college{", we can use `grep` to search for that pattern in the output. 


```
/challenge/run 2>&1|grep pwn.college{
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{09SG2dTErIJJslpQ8SX1mkkXEWK.QX1ATO0wSNyMzNzEzW}
```

### New Learnings

The `|` operator normally sends the output sent to `FD1` from the first program into `FD0` of the second file. We cannot directly send the output sent to `FD2` using the pipe operator. 

Instead, we can tell the terminal to send the output sent to `FD2` to go wherever the output sent to 'FD1` is going using 2>&1.