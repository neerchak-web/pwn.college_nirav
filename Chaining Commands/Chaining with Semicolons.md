# Chaining Commands

## Chaining with Semicolons
The easiest way to chain commands is ;. In most contexts, ; separates commands in a similar way to how Enter separates lines. So, this:
```
hacker@dojo:~$ echo COLLEGE > pwn
hacker@dojo:~$ cat pwn
COLLEGE
hacker@dojo:~$
```
Is roughly the same as this:
```
hacker@dojo:~$ echo COLLEGE > pwn; cat pwn
COLLEGE
hacker@dojo:~$
```
Basically, when you hit Enter, your shell executes your typed command and, after that command terminates, gives you the prompt to input another command. The semicolon is analogous, just without the prompt and with you entering both commands before anything is executed.

Give it a try now! In this level, you must run /challenge/pwn and then /challenge/college, chaining them with a semicolon.


### Solve
**Flag:** `pwn.college{QE6VygPShzPzu9zHtIFgJe2zjUe.QX1UDO0wSNyMzNzEzW}`

```
/challenge/pwn;/challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{QE6VygPShzPzu9zHtIFgJe2zjUe.QX1UDO0wSNyMzNzEzW}
```
### New Learnings

To run multiple commands in one line, we can chain them by sperating each command with `;`.