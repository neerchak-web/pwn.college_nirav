# Pondering Paths

## Explicit Relative Paths, From /
Previously, your relative path was "naked": it directly specified the directory to descend into from the current directory. In this level, we're going to explore more explicit relative paths.

In most operating systems, including Linux, every directory has two implicit entries that you can reference in paths: . and ... The first, ., refers right to the same directory, so the following absolute paths are all identical to each other:
```
/challenge
/challenge/.
/challenge/./././././././././
/./././challenge/././
```
The following relative paths are also all identical to each other:
```
challenge
./challenge
./././challenge
challenge/.
```
Of course, if your current working directory is /, the above relative paths are equivalent to the above absolute paths.

This challenge will get you using . in your relative paths. Get ready!



### Solve
**Flag:** `pwn.college{QvsaWmuafCrW1-pwMP9SGP5BNQR.QXwUTN0wSNyMzNzEzW}`

Attempting to execute `run` using `/challenge/run` gives a message asking the user to use the `/` directory. 

After using `cd` to change the current working directory, entering the relative path `challenge/run` gives a new message asking the user to use a relative path which starts with `.`. Since `.` refers to the current directory, we can use `./challenge/run` instead to retrieve the flag.

```
/challenge/run
Incorrect...
You are not currently in the / directory.
Please use the `cd` utility to change directory appropriately.
cd /
challenge/run
Incorrect...
This challenge must be called with a relative path that explicitly starts with a `.`!
./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{QvsaWmuafCrW1-pwMP9SGP5BNQR.QXwUTN0wSNyMzNzEzW}
```

### New Learnings
The symbol `.` in a path refers to the current directory. It can be stacked before and after a path without change in meaning.

