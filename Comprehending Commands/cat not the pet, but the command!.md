# Comprehending Commands

## cat: not the pet, but the command!
One of the most critical Linux commands is cat. cat is most often used for reading out files, like so:
```
hacker@dojo:~$ cat /challenge/DESCRIPTION.md
One of the most critical Linux commands is `cat`.
`cat` is most often used for reading out files, like so:
```
cat will concatenate (hence the name) multiple files if provided multiple arguments. For example:
```
hacker@dojo:~$ cat myfile
This is my file!
hacker@dojo:~$ cat yourfile
This is your file!
hacker@dojo:~$ cat myfile yourfile
This is my file!
This is your file!
hacker@dojo:~$ cat myfile yourfile myfile
This is my file!
This is your file!
This is my file!
```
Finally, if you give no arguments at all, cat will read from the terminal input and output it. We'll explore that in later challenges...

In this challenge, I will copy the flag to the flag file in your home directory (where your shell starts). Go read it with cat!




### Solve
**Flag:** `pwn.college{sp20EMFJtrxwN1nQaCCcor-1eNV.QXxcTN0wSNyMzNzEzW}`

The problem states that the flag is stored in a file called `flag` in our home directory. To read out the file, we can use the `cat` command while shell prompt is in the home directory.

```
cat flag
pwn.college{sp20EMFJtrxwN1nQaCCcor-1eNV.QXxcTN0wSNyMzNzEzW}
```

### New Learnings
`cat` is a command used to display the contents of one or multiple files specified as arguments. In case of multiple files, `cat` will concatenate their contents and display them sequentially.


