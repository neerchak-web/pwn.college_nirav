# Data Manipulation

## Deleting newlines
A common class of characters to remove is a line separator. This happens when you have a stream of data that you want to turn into a single line for further processing. You can specify newlines almost like any other character, by escaping them:
```
hacker@dojo:~$ echo "hello_world!" | tr _ "\n"
hello
world!
hacker@dojo:~$
```
Here, the backslash (\) signifies that the character that follows it is a standin for a character that's hard to input into the shell normally. The newline, of course, is hard to input because when you typically hit Enter, you'll run the command itself. \n is a standin for this newline, and it must be in quotes to prevent the shell interpreter itself from trying to interpret it and pass it to tr instead.

Now, let's combine this with deletion. In this challenge, we'll inject a bunch of newlines into the flag. Delete them with tr's -d flag and the escaped newline specification!

Fun fact! Want to actually replace a backslash (\) character? Because \ is the escape character, you gotta escape it! \\ will be treated as a backslash by tr. This isn't relevant to this challenge, but is a fun fact nonetheless!

### Solve
**Flag:** `pwn.college{4w5j9093g9mfuYYlB6UT4bJmm7w.0VNxEzNxwSNyMzNzEzW}`

Running `/challenge/run` will print the flag with extra `^` and `%` characters. We can pipe the output to `tr` and filter out the additional characters using the `-d` flag.

```
/challenge/run | tr -d "\n"
Your line-split flag: pwn.college{4w5j9093g9mfuYYlB6UT4bJmm7w.0VNxEzNxwSNyMzNzEzW}
```
### New Learnings

`tr` command can also take newline character as an argument. A newline character is represented in the argument as `"\n"`.