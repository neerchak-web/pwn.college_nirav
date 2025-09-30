# Chaining Commands

## Your First Shell Script
As you combine more and more commands to achieve complex effects, the length of the combined prompt quickly gets really annoying to deal with. When this happens, you can put these commands in a file, called a shell script, and run them by executing the file! For example, consider our semicolon technique:
```
hacker@dojo:~$ echo COLLEGE > pwn; cat pwn
COLLEGE
hacker@dojo:~$
```
We can create a shell script called pwn.sh (by convention, shell scripts are frequently named with a sh suffix):
```
echo COLLEGE > pwn
cat pwn
```
And then we can execute by passing it as an argument to a new instance of our shell (bash)! When a shell is invoked like this, rather than taking commands from the user, it reads commands from the file.
```
hacker@dojo:~$ ls
hacker@dojo:~$ bash pwn.sh
COLLEGE
hacker@dojo:~$ ls
pwn
hacker@dojo:~$
```
You can see that the shell script executed both commands, creating and printing the pwn file.

Now, it's your turn! Same as last level, run /challenge/pwn and then /challenge/college, but this time in a shell script called x.sh, then run it with bash!

### Solve
**Flag:** `pwn.college{496L0kC04vZVqETELL8K8la8Kg9.QXxcDO0wSNyMzNzEzW}`

To retrieve the flag, we need to run the programs `/challenge/pwn` and `/challenge/college` togeether in a shell script called `x.sh` and run it with `bash`.

We can use `ECHO` with the string '/challenge/pwn;/challenge/college` and redirect its output to the file `x.sh`.

We can then use `bash` to run the required programs by reading `x.sh`.

```
echo '/challenge/pwn;/challenge/college' > x.sh
bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{496L0kC04vZVqETELL8K8la8Kg9.QXxcDO0wSNyMzNzEzW}
```
### New Learnings

We can also run commands by putting them in `.sh` files, and invoke a new instance of the shell using `bash`.