# Chaining Commands

## Executable Shell Scripts
You have written your first shell script, but calling it via bash script.sh is a pain. Why do you need that bash?

When you invoke bash script.sh, you are, of course launching the bash command with the script.sh argument. This tells bash to read its commands from script.sh instead of standard input, and thus your shell script is executed.

It turns out that you can avoid the need to manually invoke bash. If your shell script file is executable (recall File Permissions), you can simply invoke it via its relative or absolute path! For example, if you create script.sh in your home directory and make it executable, you can invoke it via /home/hacker/script.sh or ~/script.sh or (if your working directory is /home/hacker) ./script.sh.

Try that here! Make a shellscript that will invoke /challenge/solve, make it executable, and run it without explicitly invoking bash!

### Solve
**Flag:** `pwn.college{o3Bf5HraELU4LE-Gpyu6XuJN1rJ.QX0cjM1wSNyMzNzEzW}`

To retrieve the flag, we need to run the program `/challenge/solve` in a shell script. Then we need to make the shell script executable. This can be done using `chmod`.

We can then execute the shell script without bash by using its absolute path.

```
echo '/challenge/solve' > x.sh
chmod u+x x.sh
./x.sh
Congratulations on your shell script execution! Your flag:
pwn.college{o3Bf5HraELU4LE-Gpyu6XuJN1rJ.QX0cjM1wSNyMzNzEzW}
```
### New Learnings

We can run shell scripts without `bash` by making the file executable using `chmod`.