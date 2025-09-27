# Shell Variables

## Storing Command Output
In the course of working with the shell, you will often want to store the output of some command into a variable. Luckily, the shell makes this quite easy using something called Command Substitution! Observe:
```
hacker@dojo:~$ FLAG=$(cat /flag)
hacker@dojo:~$ echo "$FLAG"
pwn.college{blahblahblah}
hacker@dojo:~$
```
Neat! Now, you practice. Read the output of the /challenge/run command directly into a variable called PWN, and it will contain the flag!

Trivia: You can also use backticks instead of $(): FLAG=`cat /flag` instead of FLAG=$(cat /flag) in the example above. This is an older format, and has some disadvantages (for example, imagine if you wanted to nest command substitutions. How would you do $(cat $(find / -name flag)) with backticks? The official stance of pwn.college is that you should use $(blah) instead of `blah`.


### Solve
**Flag:** `pwn.college{I-EYbokp-jeU9yo9iVBpzixD9O9.QX1cDN1wSNyMzNzEzW}`

To retrieve the flag, we need to read the output of `/challenge/run` into the variable `PWN` and then read the contents of `PWN`.

We can assign output from a program into a variable using `$()`. We can read the contents of a variable using `echo`.

```
PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out 
and submit it!
echo $PWN
pwn.college{I-EYbokp-jeU9yo9iVBpzixD9O9.QX1cDN1wSNyMzNzEzW}
```
### New Learnings

Variables can also take outputs of programs as values. This is done by using `$()` in the assignment statement and specifying the program inside the brackets.