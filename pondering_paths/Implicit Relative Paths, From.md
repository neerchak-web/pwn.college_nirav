# Pondering Paths

## Implicit Relative Paths, From /
Now you're familiar with the concept of referring to absolute paths and changing directories. If you put in absolute paths everywhere, then it really doesn't matter what directory you are in, as you likely found out in the previous three challenges.

However, the current working directory does matter for relative paths.

A relative path is any path that does not start at root (i.e., it does not start with /).
A relative path is interpreted relative to your current working directory (cwd).
Your cwd is the directory that your prompt is currently located at.
This means how you specify a particular file, depends on where the terminal prompt is located.

Imagine we want to access some file located at /tmp/a/b/my_file.

If my cwd is /, then a relative path to the file is tmp/a/b/my_file.
If my cwd is /tmp, then a relative path to the file is a/b/my_file.
If my cwd is /tmp/a/b/c, then a relative path to the file is ../my_file. The .. refers to the parent directory.
Let's try it here! You'll need to run /challenge/run using a relative path while having a current working directory of /. For this level, I'll give you a hint. Your relative path starts with the letter c 😊



### Solve
**Flag:** `pwn.college{YofjJQ-YZTOTjjcaRsbTz6X8Nnu.QX5QTN0wSNyMzNzEzW}`

The challenge explicitly asks us to execute `run` while having a current working directory of `/`. The current working directory can be changed using `cd` command. 

It is given that the relative path starts with the letter c. Therefore, a reasonable guess for the relative path is `challenge/run`. Entering this into the terminal while the current working directory is `/` gives us the flag.

```bash
cd /
challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{YofjJQ-YZTOTjjcaRsbTz6X8Nnu.QX5QTN0wSNyMzNzEzW}
```

### New Learnings
Relative paths are paths which don't start at root (`/`). They are relative to the current working directory. For example, if the cwd is `/a` and the path of the file to be executed is `/a/b/c/d`, the relative path is `b/c/d`.

Relative paths allow us to access files with shorter commands, rather than using the absolute path.

