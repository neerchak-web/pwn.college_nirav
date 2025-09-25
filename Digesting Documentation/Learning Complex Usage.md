# Digesting Documentation

## Learning Complex Usage
While using most commands is straightforward, the usage of some commands can get quite complex. For example, the arguments to commands like sed and awk, which we're definitely not getting into right now, are entire programs in an esoteric programming language! Somewhere on the spectrum between cd and awk are commands that take arguments to their arguments...

This sounds crazy, but you've already encountered this with the find level in Basic Commands. find has a -name argument, and the -name argument itself takes an argument specifying the name to search for. Many other commands are analogous.

Here is this level's documentation for /challenge/challenge:

Welcome to the documentation for /challenge/challenge! This program allows you to print arbitrary files to the terminal, when given the --printfile argument. The argument to the --printfile argument is the path of the flag to read. For example, /challenge/challenge --printfile /challenge/DESCRIPTION.md will print out the description of the level!

Given that documentation, go get the flag!


### Solve
**Flag:** `pwn.college{MyzQioetzbhiRzqqod3xxtjmnfX.QX1ITO0wSNyMzNzEzW}`

The challenge states that the program to be run to retrieve the flag is `/challenge/challenge`.

The documentation for the `/challenge/challenge` program states that it prints files when given the `--printfile` argument. The `--printfile` aregument takes the path of the file to be read as its argument.

Since the path of the file with the flag in it is `/flag`, the argument given to `--printfile` should be `/flag`.


```
/challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{MyzQioetzbhiRzqqod3xxtjmnfX.QX1ITO0wSNyMzNzEzW}
```

### New Learnings

Arguments to commands and programs can also take arguments. In this challenge, the program `/challenge/challenge` takes an argument `--printfile` which tells the program it has to print a file.

The path of the file to be printed is provided as an argument to `--printfile`, which itself is an argument.

