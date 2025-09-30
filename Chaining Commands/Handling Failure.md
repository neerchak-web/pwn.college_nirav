# Chaining Commands

## Handling Failure
You just learned about the && operator, which runs the second command only if the first succeeds. Now let's learn about its opposite: the || operator allows you to run a second command only if the first command fails (exits with a non-zero code). This is called the "OR" operator because either the first command succeeds OR the second command will run.

Here's the syntax:
```
hacker@dojo:~$ command1 || command2
```
This means: "Run command1, and IF it fails, then run command2."

Some examples:
```
hacker@dojo:~$ touch /file || echo "touch failed, so this runs"
touch: cannot touch '/file': Permission denied
touch failed, so this runs
hacker@dojo:~$ touch /home/hacker/file || echo "this will NOT run"
hacker@dojo:~$
```
The || operator is super useful for providing fallback commands or error handling!

In this challenge, you need to chain /challenge/first-failure and /challenge/second using the || operator. Go for it!

### Solve
**Flag:** `pwn.college{cw_iTqCwrdYRt4ePGyy1Suzy7cX.01M0MDOxwSNyMzNzEzW}`

To retrieve the flag, we need to chain the programs `/challenge/first-success` and `/challenge/second` using the `||` operator.

```
/challenge/first-failure || /challenge/second
Nice chaining! Flag: pwn.college{cw_iTqCwrdYRt4ePGyy1Suzy7cX.01M0MDOxwSNyMzNzEzW}
```
### New Learnings

Programs can be chained using the `||` operator. The terminal will only run the program after operator if the program before the operator exits with error.