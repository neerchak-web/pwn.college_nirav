# Hello Hackers

## Intro to Commands
In this challenge, you will invoke your first command! When you type a command and hit enter, the command will be invoked, as so:

hacker@dojo:~$ whoami
hacker
hacker@dojo:~$
Here, the user executed the whoami command, which simply prints the username (hacker) to the terminal. When the command terminates, the shell once again displays the prompt, ready for the next command.

In this level, invoke the hello command to get the flag! Keep in mind: commands in Linux are case sensitive: hello is different from HELLO.



### Solve
**Flag:** `pwn.college{E-q7CHPBneEq6nOU915kPcq9lDf.QX3YjM1wSNyMzNzEzW}`

After connecting to the dojo, input command `hello` to get the flag.

```hello
Success! Here is your flag:
pwn.college{E-q7CHPBneEq6nOU915kPcq9lDf.QX3YjM1wSNyMzNzEzW}
```

### New Learnings
Linux commands are case sensitive.
