# Shell Variables

## Reading Input
We'll start with reading input from the user (you). That's done using the aptly named read builtin, which reads input into a variable!

Here is an example using the -p argument, which lets you specify a prompt (otherwise, it would be hard for you, reading this now, to separate input from output in the example below):
```
hacker@dojo:~$ read -p "INPUT: " MY_VARIABLE
INPUT: Hello!
hacker@dojo:~$ echo "You entered: $MY_VARIABLE"
You entered: Hello!
```
Keep in mind, read reads data from your standard input! The first Hello!, above, was inputted rather than outputted. Let's try to be more explicit with that. Here, we annotated the beginning of each line with whether the line represents INPUT from the user or OUTPUT to the user:
```
 INPUT: hacker@dojo:~$ echo $MY_VARIABLE
OUTPUT:
 INPUT: hacker@dojo:~$ read MY_VARIABLE
 INPUT: Hello!
 INPUT: hacker@dojo:~$ echo "You entered: $MY_VARIABLE"
OUTPUT: You entered: Hello!
```
In this challenge, your job is to use read to set the PWN variable to the value COLLEGE. Good luck!


### Solve
**Flag:** `pwn.college{8qpmZkausbup25bcj4KTX-t_Y-q.QX4cTN0wSNyMzNzEzW}`

To retrieve the flag, we need to read the value to be set to the variable `PWN` from the keyboard (stdin). This can be done using the `read` command.

```
read PWN
COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{8qpmZkausbup25bcj4KTX-t_Y-q.QX4cTN0wSNyMzNzEzW}
```
### New Learnings

`read` is a builtin which reads input into the variable specified as its argument from stdin.

`read` can also be used with the `-p` flag to display a string specfied as its argument (the next argument will be the variable) before taking input from stdin. 