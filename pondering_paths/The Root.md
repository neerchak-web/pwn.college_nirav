# Pondering Paths

## The Root
Alright, so the filesystem starts at /. Under that, there are a whole mess of other directories, configuration files, programs, and, most importantly, flags. In this level, we've added a program right in /, called pwn, that will give you the flag. All you need to do for this level is to invoke this program!

You can invoke a program by providing its path on the command line. In this case, you'll be giving the exact path, starting from /, so the path would be /pwn. This style of path, one that starts with the root directory, is referred to as an "absolute path".

Start the challenge, launch a terminal, invoke the pwn program using its absolute path, and Capture that Flag! Good luck!



### Solve
**Flag:** `pwn.college{oUP79e5znRmz_tL_kxL54GAqbsG.QX4cTO0wSNyMzNzEzW}`

The flag can be retrieved by invoking a program called `pwn`. To invoke a program in a terminal session, enter the path of the program. In this case, the path is `/pwn`.

```
/pwn
BOOM!!!
Here is your flag:
pwn.college{oUP79e5znRmz_tL_kxL54GAqbsG.QX4cTO0wSNyMzNzEzW}
```

### New Learnings
A program can be executed in a terminal session by entering the absolute path of the program. The path of any file starts with `/`, the root of the filesystem.



