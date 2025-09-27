# Shell Variables

## Printing Exported Variables
There are multiple ways to access variables in bash. echo was just one of them, and we'll now learn at least one more in this challenge.

Try the env command: it'll print out every exported variable set in your shell, and you can look through that output to find the FLAG variable!

### Solve
**Flag:** `pwn.college{Yvh6hxfN72axO6xb116K4xuRKZC.QX4UTN0wSNyMzNzEzW}`

The flag is stored in one of the exported variables set in the challenge's shell. We can use `env` to display all exported variables and their contents.

This output can be piped into the input of `grep`, which can search for the pattern "pwn.college{".

```
env | grep pwn.college{
FLAG=pwn.college{Yvh6hxfN72axO6xb116K4xuRKZC.QX4UTN0wSNyMzNzEzW}
```
### New Learnings

`env` is a command which displays all exported variables set in the current shell along with their contents.