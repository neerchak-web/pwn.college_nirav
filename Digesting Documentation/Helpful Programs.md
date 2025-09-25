# Digesting Documentation

## Helpful Programs
Some programs don't have a man page, but might tell you how to run them if invoked with a special argument. Usually, this argument is --help, but it can often be -h or, in rare cases, -?, help, or other esoteric values like /? (though that latter is more frequently encountered on Windows).

In this level, you will practice reading a program's documentation with --help. Try it out!


### Solve
**Flag:** `pwn.college{sqqnYo75EAzGZ9-ibChAjOuI4MI.QX3IDO0wSNyMzNzEzW}`

Since we don't know the correct argument to `/challenge/challenge` which will display the flag, we can check whether the program has a help page. In this challenge, we have been told that the argument `--help` will display the help page.

Doing so shows the following optional arguments:
```
-h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
  ```
  We can see that the argument `-g` will display the flag if the correct value is given as argument to `-g`. To print the correct argument for `-g`, we need to give the argument `-p` to `/challenge/challenge`.

```
/challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
  /challenge/challenge -p
The secret value is: 759
/challenge/challenge -g 759
Correct usage! Your flag: pwn.college{sqqnYo75EAzGZ9-ibChAjOuI4MI.QX3IDO0wSNyMzNzEzW}
```

### New Learnings

Some programs may not have `man` pages. However, sometimes such programs display information about  what arguments the program takes and how it works when a special argument is passed.

This argument can be named something like `--help`, `-h` etc. 
