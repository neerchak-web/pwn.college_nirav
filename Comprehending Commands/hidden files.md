# Comprehending Commands

## hidden files
Interestingly, ls doesn't list all the files by default. Linux has a convention where files that start with a . don't show up by default in ls and in a few other contexts. To view them with ls, you need to invoke ls with the -a flag, as so:
```
hacker@dojo:~$ touch pwn
hacker@dojo:~$ touch .college
hacker@dojo:~$ ls
pwn
hacker@dojo:~$ ls -a
.college	pwn
hacker@dojo:~$
```
Now, it's your turn! Go find the flag, hidden as a dot-prepended file in /.


### Solve
**Flag:** `pwn.college{sx_JcmcjRQfSfL5wSwlDLrnrDMC.QXwUDO0wSNyMzNzEzW}`

It is given that the flag is hidden in the root directory in a dot prepended file. As `ls` does not show dot prepended files, we use `ls -a` instead to display all files including dot prepended ones.

After changing the the current working directory to the root directory and displaying all files, we see one of the files is dot prepended and has "flag" in it's name.

To display the contents of this file, we can use `cat` command. Doing so displays the flag.

```
cd /
ls -a
.   .dockerenv            bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
..  .flag-28155106906025  boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
cat .flag-28155106906025
pwn.college{sx_JcmcjRQfSfL5wSwlDLrnrDMC.QXwUDO0wSNyMzNzEzW}
```

### New Learnings

The `ls` command, by default, does not display dot prepended files or directories in the specified directory. To display all files, including dot prepended files, we need to invoke `ls` with the `-a` flag.

