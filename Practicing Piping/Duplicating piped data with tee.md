# Practicing Piping

## Duplicating piped data with tee
When you pipe data from one command to another, you of course no longer see it on your screen. This is not always desired: for example, you might want to see the data as it flows through between your commands to debug unintended outcomes (e.g., "why did that second command not work???").

Luckily, there is a solution! The tee command, named after a "T-splitter" from plumbing pipes, duplicates data flowing through your pipes to any number of files provided on the command line. For example:
```
hacker@dojo:~$ echo hi | tee pwn college
hi
hacker@dojo:~$ cat pwn
hi
hacker@dojo:~$ cat college
hi
hacker@dojo:~$
```
As you can see, by providing two files to tee, we ended up with three copies of the piped-in data: one to stdout, one to the pwn file, and one to the college file. You can imagine how you might use this to debug things going haywire:
```
hacker@dojo:~$ command_1 | command_2
Command 2 failed!
hacker@dojo:~$ command_1 | tee cmd1_output | command_2
Command 2 failed!
hacker@dojo:~$ cat cmd1_output
Command 1 failed: must pass --succeed!
hacker@dojo:~$ command_1 --succeed | command_2
Commands succeeded!
```
Now, you try it! This process' /challenge/pwn must be piped into /challenge/college, but you'll need to intercept the data to see what pwn needs from you!


### Solve
**Flag:** `pwn.college{sLIAcQtf5ToREX_74DPOzoyk7Cf.QXxITO0wSNyMzNzEzW}`

We can connect output channel from `/challenge/pwn` into input channel of `/challenge/college` using pipe (`|`) operator. 

To intercept the data, we can first pipe the output from `/challenge/pwn` into `tee file`. This will write the output into the file `file`, and will also send that output to the output channel of `tee`.

We can again pipe the output channel of `tee` to the input channel of `/challenge/college`.

After doing so, we can read the contents of `file` using `cat` to find the secret argument required to retrieve the flag.
```
/challenge/pwn | tee file | /challenge/college
Processing...
The input to 'college' does not contain the correct secret code! This code 
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the 
output of 'pwn' and figure out what the code needs to be.
cat file
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "sLIAcQtf"
/challenge/pwn --secret sLIAcQtf | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{sLIAcQtf5ToREX_74DPOzoyk7Cf.QXxITO0wSNyMzNzEzW}
```

### New Learnings

`tee` is a command which reads from the standard input channel, writes it into the files specified as its arguments, and also outputs the same data into the standard output channel.