# Processes and Jobs

## Killing Processes 
You've launched processes, you've viewed processes, now you will learn to terminate processes! In Linux, this is done using the aggressively-named kill command. With default options (which is all we'll cover in this level), kill will terminate a process in a way that gives it a chance to get its affairs in order before ceasing to exist.

Let's say you had a pesky sleep process (sleep is a program that simply hangs out for the number of seconds specified on the commandline, in this case, 1337 seconds) that you launched in another terminal, like so:
```
hacker@dojo:~$ sleep 1337
```
How do we get rid of it? You use kill to terminate it by passing the process identifier (the PID from ps) as an argument, like so:
```
hacker@dojo:~$ ps -e | grep sleep
 342 pts/0    00:00:00 sleep
hacker@dojo:~$ kill 342
hacker@dojo:~$ ps -e | grep sleep
hacker@dojo:~$
```
Now, it's time to terminate your first process! In this challenge, /challenge/run will refuse to run while /challenge/dont_run is running! You must find the dont_run process and kill it. If you fail, pwn.college will disavow all knowledge of your mission. Good luck.


### Solve
**Flag:** `pwn.college{Ahdf5IVESseDtxwYcc0vAqoSRP0.QXyQDO0wSNyMzNzEzW}`

To retrieve the flag, we need to run `/challenge/run`. However, `/challenge/run` won't run while `/challenge/dont_run` is running. To terminate it, we can use the `kill` command. To get the `PID` of `/challenge/dont_run`, we can use the `ps -ef` command.

```
ps -ef | grep /challenge/dont_run
hacker       136     135  0 13:07 ?        00:00:00 /challenge/dont_run
hacker       163     152  0 13:08 pts/0    00:00:00 grep --color=auto /challenge/dont_run
kill 136
/challenge/run
Great job! Here is your payment:
pwn.college{Ahdf5IVESseDtxwYcc0vAqoSRP0.QXyQDO0wSNyMzNzEzW}
```
### New Learnings

`kill` is a command used to terminate running processes. It takes the process ID as its argument.


