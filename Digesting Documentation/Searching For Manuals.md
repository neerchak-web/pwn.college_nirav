# Digesting Documentation

## Searching For Manuals
This level is tricky: it hides the manpage for the challenge by randomizing its name. Luckily, all of the manpages are gathered in a searchable database, so you'll be able to search the man page database to find the hidden challenge man page! To figure out how to search for the right manpage, read the man page manpage by doing: man man!

HINT 1: man man teaches you advanced usage of the man command itself, and you must use this knowledge to figure out how to search for the hidden manpage that will tell you how to use /challenge/challenge

HINT 2: though the manpage is randomly named, you still actually use /challenge/challenge to get the flag!


### Solve
**Flag:** `pwn.college{AXJeHzX07vU3J1ZyZBa6u9WyFKg.QX2EDO0wSNyMzNzEzW}`

The manual for the challenge is not given to us. First, we need to find a method to search all the manual pages in the system. 

To find the required argument to the `man` command which will allow us to search for a manual page, we need to read the manual page for the `man` command. 

The argument to `man` we're looking for involves searching, which means the pattern "search" most likely occurs in the description of the argument. We can search for the pattern "search" in the manual page for `man` by hitting `/`.

By doing so, we see that the `man` command takes an argument `-k`, which itself takes a pattern as an argument. It will search the short descriptions and manual page names for the pattern.

Since we need to use `/challenge/challenge` with some unknown argument to get the flag, we should search for manual pages named `challenge`. Doing so displays only one matching entry named `ezvyauygwy`.

Opening the manual page for `ezvyauygwy`, we see that `/challenge/challenge` will print the flag when the argument `--ezvyau 073` is given to it.

```
man man
man -k challenge
ezvyauygwy (1)       - print the flag!
man ezvyauygwy
/challenge/challenge --ezvyau 073
Correct usage! Your flag: pwn.college{AXJeHzX07vU3J1ZyZBa6u9WyFKg.QX2EDO0wSNyMzNzEzW}
```

### New Learnings

`man` command takes an argument `-k` which itself takes a pattern as an argument. It will search the short descriptions and manual page names for the pattern. 
