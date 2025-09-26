# Practicing Piping

## Grepping stored results
You know how to run commands, how to redirect their output (e.g., >), and how to search through the resulting file (e.g., grep). Let's put this together!

In preparation for more complex levels, we want you to:

Redirect the output of /challenge/run to /tmp/data.txt.
This will result in a hundred thousand lines of text, with one of them being the flag, in /tmp/data.txt.
grep that for the flag!

### Solve
**Flag:** `pwn.college{sKUxr2nEQAPXEGraJ918P5cyoci.QX4EDO0wSNyMzNzEzW}`

Running the program `/challenge/run` gives us the required flag. However, for this challenge, the output of `/challenge/run` needs to be redirected to `/tmp/data.txt`. This can be done using `>`.

The output of `/challenge/run` is too vast to search manually. Since we know all flags start with the pattern "pwn.college",we can use the `grep` command to search for that pattern in `/tmp/data.txt`

```
/challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
grep pwn.college /tmp/data.txt
pwn.college{sKUxr2nEQAPXEGraJ918P5cyoci.QX4EDO0wSNyMzNzEzW}
```

### New Learnings

This challenge combines the concept of redirecting outputs and the `grep` command from the previous module.