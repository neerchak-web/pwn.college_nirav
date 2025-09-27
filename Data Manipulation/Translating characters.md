# Data Manipulation

## Translating characters
One of the purposes of piping data is to modify it. Many Linux commands will help you modify data in really cool ways. One of these is tr, which translates characters it receives over standard input and prints them to standard output.

In its most basic usage, tr translates the character provided in its first argument to the character provided in its second argument:
```
hacker@dojo:~$ echo OWN | tr O P
PWN
hacker@dojo:~$
```
It can also handle multiple characters, with the characters in different positions of the first argument replaced with associated characters in the second argument.
```
hacker@dojo:~$ echo PWM.COLLAGE | tr MA NE
PWN.COLLEGE
hacker@dojo:~$
```
Now, you try it! In this level, /challenge/run will print the flag but will swap the casing of all characters (e.g., A will become a and vice-versa). Can you undo it with tr and get the flag?

### Solve
**Flag:** `pwn.college{cYTPr-7enZLHXQx0BQYg8JqEi0t.01MxEzNxwSNyMzNzEzW}`

Running `/challenge/run` will print the flag with reversed casing. We can pipe the output to `tr` and translate each uppercase character to lowercase, and vice versa.

The first argument to `tr` should be all uppercase characters followed by lowercase characters. The second argument should be all lowercase characters followed by uppercase characters. This way, every lowercase character in the first argument is at the same position as its uppercase value in the second argument and vice versa.

```
/challenge/run | tr QWERTYUIOPASDFGHJKLZXCVBNMqwertyuiopasdfghjklzxcvbnm qwertyuiopasdfghjklzxcvbnmQWERTYUIOPASDFGHJKLZXCVBNM
yOUR CASE-SWAPPED FLAG:
pwn.college{cYTPr-7enZLHXQx0BQYg8JqEi0t.01MxEzNxwSNyMzNzEzW}
```
### New Learnings

`tr` is a command which takes input from stdin, replaces the characters from its first argument in the input with the corresponding characters from its second argument, and prints it in stdout.