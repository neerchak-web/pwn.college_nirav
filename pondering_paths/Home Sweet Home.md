# Pondering Paths

## Home Sweet Home
Every user has a home directory, typically under /home in the filesystem. In the dojo, you are the hacker user, and your home directory is /home/hacker. The home directory is typically where users store most of their personal files. As you make your way through pwn.college, this is where you'll store most of your solutions.

Typically, your shell session will start with your home directory as your current working directory. Consider the initial prompt:
```
hacker@dojo:~$
```
The ~ in this prompt is the current working directory, with ~ being shorthand for /home/hacker. Bash provides and uses this shorthand because, again, most of your time will be spent in your home directory. Thus, whenever bash sees ~ provided as the start of an argument in a way consistent with a path, it will expand it to your home directory. Consider:
```
hacker@dojo:~$ echo LOOK: ~
LOOK: /home/hacker
hacker@dojo:~$ cd /
hacker@dojo:/$ cd ~
hacker@dojo:~$ cd ~/asdf
hacker@dojo:~/asdf$ cd ~/asdf
hacker@dojo:~/asdf$ cd ~
hacker@dojo:~$ cd /home/hacker/asdf
hacker@dojo:~/asdf$
```
Note that the expansion of ~ is an absolute path, and only the leading ~ is expanded. This means, for example, that ~/~ will be expanded to /home/hacker/~ rather than /home/hacker/home/hacker.

Fun fact: cd will use your home directory as the default destination:
```
hacker@dojo:~$ cd /tmp
hacker@dojo:/tmp$ cd
hacker@dojo:~$
```
Now it's your turn to play! In this challenge, /challenge/run will write a copy of the flag to any file you specify as an argument on the commandline, with these constraints:

Your argument must be an absolute path.
The path must be inside your home directory.
Before expansion, your argument must be three characters or less.
Again, you must specify your path as an argument to /challenge/run as so:
```
hacker@dojo:~$ /challenge/run YOUR_PATH_HERE
```


### Solve
**Flag:** `pwn.college{QvIKfJ0J-IJlrBm0PJNtMM5J7Q1.QXzMDO0wSNyMzNzEzW}`

The problem states that `/challenge/run` will write a copy of the flag to any file we specifiy as an argument, provided that the argument is an absolute path in the home directory less than three characters before expansion.

Any absolute path in the home directory must be of the form `~/abcd...`. `~/` itself is two characters (before expansion). Therefore, we can choose any single-character file name. Thus, the argument to `/challenge/run` can be something like `~/f`.




```
/challenge/run ~/f
Writing the file to /home/hacker/f!
... and reading it back to you:
pwn.college{QvIKfJ0J-IJlrBm0PJNtMM5J7Q1.QXzMDO0wSNyMzNzEzW}
```

### New Learnings
In Linux, the path of the home directory of a user is represented by `~`. If the home directory is `/a/b`, then `~` in any file path is a shorthand for `/a/b`. For example, `~/c/d` expands to `/a/b/c/d`. 

This is useful as it allows users to access and modify files in their home directory without having to change their `cwd` or type the absolute path each time.

