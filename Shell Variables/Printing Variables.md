# Shell Variables

## Printing Variables
Let's start with printing variables out. The /challenge/run program will not, and cannot, give you the flag, but that's okay, because the flag has been put into the variable called "FLAG"! Just have your shell print it out!

You can accomplish this using a number of ways, but we'll start with echo. This command just prints stuff. For example:
```
hacker@dojo:~$ echo Hello Hackers!
Hello Hackers!
```
You can also print out variables with echo, by prepending the variable name with a $. For example, there is a variable, PWD, that always holds the current working directory of the current shell. You print it out as so:
```
hacker@dojo:~$ echo $PWD
/home/hacker
```
Now it's your turn. Have your shell print out the FLAG variable and solve this challenge!


### Solve
**Flag:** `pwn.college{MKfr0xfnQ1ylywT4gqA2C8Wesif.QX3UTN0wSNyMzNzEzW}`

The required flag is stored in the variable `FLAG`. We can use `echo` to display its contents. 

```
echo $FLAG
pwn.college{MKfr0xfnQ1ylywT4gqA2C8Wesif.QX3UTN0wSNyMzNzEzW}
```
### New Learnings

The contents of a variable can be displayed using `echo`. The argument should the variable name prepended with the `$` symbol.