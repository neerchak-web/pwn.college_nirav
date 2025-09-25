# Digesting Documentation

## Help for Builtins
Some commands, rather than being programs with man pages and help options, are built into the shell itself. These are called builtins. Builtins are invoked just like commands, but the shell handles them internally instead of launching other programs. You can get a list of shell builtins by running the builtin help, as so:
```
hacker@dojo:~$ help
```
You can get help on a specific one by passing it to the help builtin. Let's look at a builtin that we've already used earlier, cd!
```
hacker@dojo:~$ help cd
cd: cd [-L|[-P [-e]] [-@]] [dir]
    Change the shell working directory.
    
    Change the current directory to DIR.  The default DIR is the value of the
    HOME shell variable.
...
```
Some good information! In this challenge, we'll practice using help to look up help for builtins. This challenge's challenge command is a shell builtin, rather than a program. Like before, you need to lookup its help to figure out the secret value to pass to it!


### Solve
**Flag:** `pwn.college{caEob1vrUacBV7vbpjL-u6_Sf-2.QX0ETO0wSNyMzNzEzW}`

This time, `challenge` is a builtin. To look up information about builtins, we use the `help` command instead of `man`. Using `help` we see that `challenge` will display the flag when `--secret caEob1vr` is given as argument.

```
help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!
    
    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "caEob1vr".
challenge --secret caEob1vr
Correct! Here is your flag!
pwn.college{caEob1vrUacBV7vbpjL-u6_Sf-2.QX0ETO0wSNyMzNzEzW}
```

### New Learnings

Builtins are commands which are not run as programs, but are built into the shell itself. Their documentation isn't accessed with `man`. To get information about how a builtin works, we use the `help` command instead, with the builtin provided as the argument.
