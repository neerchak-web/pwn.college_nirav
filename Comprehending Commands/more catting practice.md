# Comprehending Commands

## more catting practice
You can specify all sorts of paths as arguments to commands, and we'll practice some more with cat. In this level, I'll put the flag in some crazy directory, and I will not allow you to change directories with cd, so no cat flag for you. You must retrieve the flag by absolute path, wherever it is.


### Solve
**Flag:** `pwn.college{Mfgw4HEd3IeFihimhNyTyevn2iP.QXwITO0wSNyMzNzEzW}`

Running the terminal displays a message containing the absolute path to the file with the flag in it. Since the challenge asks us not to change the `cwd`, we can use the `cat` command with the given absolute path as an argument to retrieve the flag.

```
You cannot use the 'cd' command in this level, and must retrieve the flag by 
absolute path. Plus, I hid the flag in a different directory! You can find it 
in the file /lib/x86_64-linux-gnu/gap/flag. Go cat it out **without** cding 
into that directory!
cat /lib/x86_64-linux-gnu/gap/flag
pwn.college{Mfgw4HEd3IeFihimhNyTyevn2iP.QXwITO0wSNyMzNzEzW}
```

### New Learnings
The `cat` command accepts any absolute path as a valid argument, no matter how many subdirectories it contains.

