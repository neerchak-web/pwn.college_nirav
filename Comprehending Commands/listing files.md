# Comprehending Commands

## listing files
So far, we've told you which files to interact with. But directories can have lots of files (and other directories) inside them, and we won't always be here to tell you their names. You'll need to learn to list their contents using the ls command!

ls will list files in all the directories provided to it as arguments, and in the current directory if no arguments are provided. Observe:
```
hacker@dojo:~$ ls /challenge
run
hacker@dojo:~$ ls
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
hacker@dojo:~$ ls /home/hacker
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
hacker@dojo:~$
```
In this challenge, we've named /challenge/run with some random name! List the files in /challenge to find it.


### Solve
**Flag:** `pwn.college{ADloF0b5BX20jkwsXdOeeofIv-k.QX4IDO0wSNyMzNzEzW}`

It is given that the file to be run to retrieve the flag is located in `/challenge`. We can list all the files in `/challenge` using the `ls` command. 

Entering `ls /challenge` displays two files. The first file `31779-renamed-run-28878` has "run" in it's full name, making it more likely to be the required file. 

Running the file by entering `/challenge/31779-renamed-run-28878` displays the flag.

```
ls /challenge
31779-renamed-run-28878  DESCRIPTION.md
/challenge/31779-renamed-run-28878
Yahaha, you found me! Here is your flag:
pwn.college{ADloF0b5BX20jkwsXdOeeofIv-k.QX4IDO0wSNyMzNzEzW}
```

### New Learnings

`ls` is a command which takes one or more paths as arguments and displays all the files and directories located in those paths.

When no argument is given, `ls` displays the files and directories located in the current working directory.

