# File Globbing

## Mixing globs
Now, let's put the previous levels together! We put a few happy, but diversely-named files in /challenge/files. Go cd there and, using the globbing you've learned, write a single, short (6 characters or less) glob that (when passed as an argument to /challenge/run) will match the files "challenging", "educational", and "pwning"!

### Solve
**Flag:** `pwn.college{UeIHqrs7WUvHFwS-qR9SLg9dCVz.QX1IDO0wSNyMzNzEzW}`

To retrieve the flag, we need to change the current working directory to `/challenge/files` and run `/challenge/run` with a six-character argument that matches the files `challenging`, `educational`, and `pwning`.

We can check if there are any other files that start with the letter `c`, `e` or `p` using the command `ls [cpe]*`. Doing so only displays the required files, and no additional matches.

Therefore, the required argument is also `[cpe]*`.

```
cd /challenge/files
ls [cpe]*
challenging  educational  pwning
/challenge/run [cpe]*
You got it! Here is your flag!
pwn.college{UeIHqrs7WUvHFwS-qR9SLg9dCVz.QX1IDO0wSNyMzNzEzW}
```

### New Learnings

This challenge combines the concept of `*` and `[]` globs, and multiple globs.
