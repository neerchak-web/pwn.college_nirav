# Pondering Paths

## Program and Absolute Paths
Let's explore a slightly more complicated path! Except for in the previous level, challenges in pwn.college are in the challenge directory and the challenge directory is, in turn, right in the root directory (/). The path to the challenge directory is, thus, /challenge. The name of the challenge program in this level is run, and it lives in the /challenge directory. Thus, the path to the run challenge program is /challenge/run.

This challenge again requires you to execute it by invoking its absolute path. You'll want to execute the run file that is in the challenge directory that is, in turn, in the / directory. If you invoke the challenge correctly, it will give you the flag. Good luck!



### Solve
**Flag:** `pwn.college{wMMFN_ZqWk1JjgvcQW0pKUcaMNI.QX1QTN0wSNyMzNzEzW}`

The flag can be retrieved by executing the program `run`. `run` is located in the `challenge` directory. `challenge` is located in the root directory (`/`). Therefore, the absolute path of `run` is `/challenge/run`. This is to be entered into the terminal to execute `run`.

```
/challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{wMMFN_ZqWk1JjgvcQW0pKUcaMNI.QX1QTN0wSNyMzNzEzW}
```

### New Learnings
A file not located directly in the root directory can be executed in the terminal using its absolute path. In general, the absolute path of a file `f` is of the form: 

`/sub_directory1/sub_directory2.../f`

The path starts from the root (`/`), and includes all directories (`/sub_directory1`, `/sub_directory2`, etc.) leading to the file.
