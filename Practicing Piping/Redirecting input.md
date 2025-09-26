# Practicing Piping

## Redirecting input
Just like you can redirect output from programs, you can redirect input to programs! This is done using <, as so:
```
hacker@dojo:~$ echo yo > message
hacker@dojo:~$ cat message
yo
hacker@dojo:~$ rev < message
oy
```
You can do interesting things with a lot of different programs using input redirection! In this level, we will practice using /challenge/run, which will require you to redirect the PWN file to it and have the PWN file contain the value COLLEGE! To write that value to the PWN file, recall the prior challenge on output redirection from echo!



### Solve
**Flag:** `pwn.college{0ablFe_c55vxuqCmyhP9GPZMOBI.QXwcTN0wSNyMzNzEzW}`

Running the program `/challenge/run` gives us the required flag. However, for this challenge `/challenge/run` needs to take the input "COLLEGE" to retrieve the flag. Furthermore, the program is only allowed to take input from the file `PWN`.

Therefore, first we must write the pattern "COLLEGE" into the file `PWN`. This can be done using `echo` and `>`.

To take input from a file, we can use `<`.

```
echo COLLEGE > PWN
/challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read 
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{0ablFe_c55vxuqCmyhP9GPZMOBI.QXwcTN0wSNyMzNzEzW}
```

### New Learnings

The `<` character provides input to the program specified before it from the file specified after it.
