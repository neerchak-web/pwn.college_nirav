# Chaining Commands

## Scripting with Arguments
You've learned how to make shell scripts, but so far they've just been lists of commands. Scripts become much more powerful when they can accept arguments! This might look like:
```
hacker@dojo:~$ bash myscript.sh hello world
```
The script can access these arguments using special variables:

$1 contains the first argument ("hello")
$2 contains the second argument ("world")
$3 would contain the third argument (if there had been one)
...and so on
Here's a simple example:
```
hacker@dojo:~$ cat myscript.sh
#!/bin/bash
echo "First argument: $1"
echo "Second argument: $2"
hacker@dojo:~$ bash myscript.sh hello world
First argument: hello
Second argument: world
hacker@dojo:~$
```
For this challenge, you need to write a script at /home/hacker/solve.sh that:

Takes two arguments
Outputs them in REVERSE order (second argument first, then the first argument)
For example:
```
hacker@dojo:~$ bash /home/hacker/solve.sh pwn college
college pwn
hacker@dojo:~$
```
Once your script works correctly, run /challenge/run to get your flag!


### Solve
**Flag:** `pwn.college{IakULwYkoWE8Ygb7sK37E4--tnm.0VNzMDOxwSNyMzNzEzW}`

To retrieve the flag, we need to make a shell script that takes two arguments and output them in reverse. We can use the positional arguments `$2` followed by `$1` to display secondargument before first.

```
hacker@chaining~scripting-with-arguments:~$ echo 'echo $2 $1' > solve.sh
hacker@chaining~scripting-with-arguments:~$ bash solve.sh hello world
world hello
hacker@chaining~scripting-with-arguments:~$ /challenge/run
Correct! Your script properly reversed the arguments.
Here's your flag:
pwn.college{IakULwYkoWE8Ygb7sK37E4--tnm.0VNzMDOxwSNyMzNzEzW}
```
### New Learnings

Shell scripts can accept arguments using special variables in the script. In the script, `$1` represents the first argument, `$2` represents second and so on.