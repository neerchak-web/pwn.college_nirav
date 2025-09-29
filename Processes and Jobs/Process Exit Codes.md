# Processes and Jobs

## Process Exit Codes 
Every shell command, including every program and every builtin, exits with an exit code when it finishes running and terminates. This can be used by the shell, or the user of the shell (that's you!) to check if the process succeeded in its functionality (this determination, of course, depends on what the process is supposed to do in the first place).

You can access the exit code of the most recently-terminated command using the special ? variable (don't forget to prepend it with $ to read its value!):
```
hacker@dojo:~$ touch test-file
hacker@dojo:~$ echo $?
0
hacker@dojo:~$ touch /test-file
touch: cannot touch '/test-file': Permission denied
hacker@dojo:~$ echo $?
1
hacker@dojo:~$
```
As you can see, commands that succeed typically return 0 and commands that fail typically return a non-zero value, most commonly 1 but sometimes an error code that identifies a specific failure mode.

In this challenge, you must retrieve the exit code returned by /challenge/get-code and then run /challenge/submit-code with that error code as an argument. Good luck!


### Solve
**Flag:** `pwn.college{MsTFfmcsP3zxvvjViMDTERk1LqV.QX5YDO1wSNyMzNzEzW}`

To retrieve the flag, we need to run `/challenge/get-code`, and then run `/challenge/submit-code` with the argument as the exit code from running `/challenge/get-code`.

To get the exit code of the last run command, we can use `echo $?`.

```
/challenge/get-code
Exiting with an error code!
echo $? 
219
/challenge/submit-code 219
CORRECT! Here is your flag:
pwn.college{MsTFfmcsP3zxvvjViMDTERk1LqV.QX5YDO1wSNyMzNzEzW}
```
### New Learnings

`echo $?` displays the exit code of the last run command.

