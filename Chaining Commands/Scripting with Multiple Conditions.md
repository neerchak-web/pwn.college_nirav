# Chaining Commands

## Scripting with Multiple Conditions
You've learned how to use a single if statement to check a condition. But what if you need to check multiple conditions? You can use elif (short for else if):
```
if [ "$1" == "one" ]
then
    echo "1"
elif [ "$1" == "two" ]
then
    echo "2"
elif [ "$1" == "three" ]
then
    echo "3"
else
    echo "unknown"
fi
```
Note that you do need a then after the elif, just like the if. As before the else at the end catches everything that didn't match.

For this challenge, write a script at /home/hacker/solve.sh that:

Takes one argument
If the argument is "hack", output "the planet"
If the argument is "pwn", output "college"
If the argument is "learn", output "linux"
For any other input, output "unknown"
Example:
```
hacker@dojo:~$ bash /home/hacker/solve.sh hack
the planet
hacker@dojo:~$ bash /home/hacker/solve.sh pwn
college
hacker@dojo:~$ bash /home/hacker/solve.sh learn
linux
hacker@dojo:~$ bash /home/hacker/solve.sh foo
unknown
hacker@dojo:~$
```
Once your script works correctly, run /challenge/run to get your flag!

### Solve
**Flag:** `pwn.college{s8CaOAQm-j7ASyZp1D8tuH_r3rK.0FOzMDOxwSNyMzNzEzW}`

The required shell script is:
```
if [ "$1" == "hack" ]
then
    echo "the planet"
elif [ "$1" == "pwn" ]
then
    echo "college"
elif [ "$1" == "learn" ]
then
    echo "linux"
else
    echo "unknown"
fi
```
```
/challenge/run
Correct! Your script properly handles all the conditions with elif.
Here's your flag:
pwn.college{s8CaOAQm-j7ASyZp1D8tuH_r3rK.0FOzMDOxwSNyMzNzEzW}
```
### New Learnings

Multiple conditional statements to be evaluated one after another can be coded using `elif` statements between `if` and `else`.