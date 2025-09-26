# File Globbing

## Multiple options for tab completion
Consider the following situation:
```
hacker@dojo:~$ ls
flag  flamingo  flowers
hacker@dojo:~$ cat f<TAB>
```
There are multiple options! What happens?

What happens varies based on the specific shell and its options. By default bash will auto-expand until the first point when there are multiple options (in this case, fl). When you hit tab a second time, it'll print out those options. Other shells and configurations, instead, will cycle through the options.

This challenge has a /challenge/files directory with a bunch of files starting with pwncollege. Tab-complete from /challenge/files/p or so, and make your way to the flag!


### Solve
**Flag:** `pwn.college{Y1Lnski34qoZPD1HNHIosMP1q7t.0lN0EzNxwSNyMzNzEzW}`

We need to read to contents of a file located in `/challenge/files` that starts with `p`. We can start with the command `cat /challenge/files/p` and use tab autocomplete.

Hitiing `tab` once expands the original command to `challenge/files/pwn`. Hitiing `tab` again displays multiple files, out of which one is named `pwncollege-flag`.

Now that we know the name of the file with the flag, we can use `cat` to read its contents.

```
cat /challenge/files/pwn
pwn                    pwn-the-planet         pwncollege-flag        pwncollege-flyswatter  
pwn-college            pwncollege-family      pwncollege-flamingo    pwncollege-hacking
cat /challenge/files/pwncollege-flag
pwn.college{Y1Lnski34qoZPD1HNHIosMP1q7t.0lN0EzNxwSNyMzNzEzW}
```

### New Learnings

If there are multiple possible matches while using tab autocomplete, bash will auto-expand the command until the character from which all the matches start diverging. 

Hitting `tab` again will display all the possible matches.
