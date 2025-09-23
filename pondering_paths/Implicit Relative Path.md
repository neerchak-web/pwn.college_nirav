# Pondering Paths

## Implicit Relative Path
In this level, we'll practice referring to paths using . a bit more. This challenge will need you to run it from the /challenge directory. Here, things get slightly tricky.

Linux explicitly avoids automatically looking in the current directory when you provide a "naked" path. Consider the following:
```
hacker@dojo:~$ cd /challenge
hacker@dojo:/challenge$ run
```
This will not invoke /challenge/run. This is actually a safety measure: if Linux searched the current directory for programs every time you entered a naked path, you could accidentally execute programs in your current directory that happened to have the same names as core system utilities! As a result, the above commands will yield the following error:
```
bash: run: command not found
```
We'll explore the mechanisms behind this concept later, but in this challenge, we'll learn how to explicitly use relative paths to launch run in this scenario. The way to do this is to tell Linux that you explicitly want to execute a program in the current directory, using . like in the previous levels. Give it a try now!



### Solve
**Flag:** `pwn.college{E_s4bxoIQ5LauYiusM8QLUiv7d0.QXxUTN0wSNyMzNzEzW}`

The challenge requires us to execute `run` in the `challenge` directory. Using `cd` we can enter the `challenge` directory. 

The challenge asks us to not directly enter `run` into the prompt. Instead, we must explicitly specify to the terminal to look for `run` in the current directory (`challenge`) using `./run`.

This ensures that the terminal executes the `run` program located in the current directory, rather than searching for it anywhere else.

```bash
cd /challenge
./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{E_s4bxoIQ5LauYiusM8QLUiv7d0.QXxUTN0wSNyMzNzEzW}
```

### New Learnings
If we just enter a file name into the prompt, it does not automatically look for it in the current working directory. Instead, it looks for it in a list of directories listed in an environment variable called $PATH.

The current working directory is not included in $PATH for security reasons. This prevents the system from accidentally running malicious files located in the `cwd` which have the same name as files located in $PATH.
