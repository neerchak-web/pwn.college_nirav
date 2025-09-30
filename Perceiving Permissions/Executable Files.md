# Perceiving Permissions

## Executable Files
So far, you have mostly been dealing with read permissions. This makes sense, because you have been making the /flag file readable to read it. In this level, we will explore execute permissions.

When you invoke a program, such as /challenge/run, Linux will only actually execute it if you have execute-access to the program file. Consider:
```
hacker@dojo:~$ ls -l /challenge/run
-rwxr-xr-x 1 root root    0 May 22 13:42 /challenge/run
hacker@dojo:~$ /challenge/run
Successfully ran the challenge!
hacker@dojo:~$
```
In this case, /challenge/run runs because it is executable by the hacker user. Because the file is owned by the root user and root group, this requires that the execute bit is set on the other permissions. If we remove these permissions, the execution will fail!
```
hacker@dojo:~$ chmod o-x /challenge/run
hacker@dojo:~$ ls -l /challenge/run
-rwxr-xr-- 1 root root    0 May 22 13:42 /challenge/run
hacker@dojo:~$ /challenge/run
bash: /challenge/run: Permission denied
hacker@dojo:~$
```
In this challenge, the /challenge/run program will give you the flag, but you must first make it executable! Remember your chmod, and get /challenge/run to tell you the flag!


### Solve
**Flag:** `pwn.college{gu89QcFzgxduK2bUQjg6_ybfaAW.QXyEjN0wSNyMzNzEzW}`

To retrieve the flag, we need to run `/challenge/run`.

In this level we will be allowed to use `chmod` without root access. We can grant execute permission for `/challenge/run` to all users, using `chmod a+x /challenge/run`.

```
chmod a+x /challenge/run
/challenge/run
Successful execution! Here is your flag:
pwn.college{gu89QcFzgxduK2bUQjg6_ybfaAW.QXyEjN0wSNyMzNzEzW}
```
### New Learnings

`chmod` command is used to change file permissions. File permissions involve read, write, and execute permissions for specific users or groups.
