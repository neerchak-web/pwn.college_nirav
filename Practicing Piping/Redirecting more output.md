# Practicing Piping

## Redirecting more output
Aside from redirecting the output of echo, you can, of course, redirect the output of any command. In this level, /challenge/run will once more give you a flag, but only if you redirect its output to the file myflag. Your flag will, of course, end up in the myflag file!

You'll notice that /challenge/run will still happily print to your terminal, despite you redirecting stdout. That's because it communicates its instructions and feedback over standard error, and only prints the flag over standard out!


### Solve
**Flag:** `pwn.college{Q3E9hPnQd9GXlfClwzlERDJn1dS.QX1YTN0wSNyMzNzEzW}`

Running the program `/challenge/run` gives us the required flag. However, for this challenge, we have been asked to redirect the output of the program into a file named `myflag`. This can be done using the `>` character.

After redirecting the output, we can read it from the file `myflag` using `cat`.
```
/challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{Q3E9hPnQd9GXlfClwzlERDJn1dS.QX1YTN0wSNyMzNzEzW}
```

### New Learnings

The `>` character can also be used to redirect the outputs from commands.
