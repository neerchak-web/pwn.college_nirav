# File Globbing

## Multiple globs
So far, you've specified one glob at a time, but you can do more! Bash supports the expansion of multiple globs in a single word. For example:
```
hacker@dojo:~$ cat /*fl*
pwn.college{YEAH}
hacker@dojo:~$
```
What happens above is that the shell looks for all files in / that start with anything (including nothing), then have an f and an l, and end in anything (including ag, which makes flag).

Now you try it. We put a few happy, but diversely-named files in /challenge/files. Go cd there and run /challenge/run, providing a single argument: a short (3 characters or less) globbed word with two * globs in it that covers every word that contains the letter p.


### Solve
**Flag:** `pwn.college{U8jQ5-bXJJ4P96j8WwFLG_UiuBJ.0lM3kjNxwSNyMzNzEzW}`

To retrieve the flag, we need to change the current working directory to `/challenge/files` and run `/challenge/run` with a three-character argument that contains two `*` globs and covers every word that contains the letter `p`.

Clearly, the argument `*p*` meets all the required conditions.

```
cd /challenge/files
/challenge/run *p*
You got it! Here is your flag!
pwn.college{U8jQ5-bXJJ4P96j8WwFLG_UiuBJ.0lM3kjNxwSNyMzNzEzW}
```

### New Learnings

Arguments can contain more than one glob. Multiple globs can be expanded in a single word.
