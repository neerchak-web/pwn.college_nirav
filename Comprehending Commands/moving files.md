# Comprehending Commands

## moving files
You can also move files around with the mv command. The usage is simple:
```
hacker@dojo:~$ ls
my-file
hacker@dojo:~$ cat my-file
PWN!
hacker@dojo:~$ mv my-file your-file
hacker@dojo:~$ ls
your-file
hacker@dojo:~$ cat your-file
PWN!
hacker@dojo:~$
```
This challenge wants you to move the /flag file into /tmp/hack-the-planet (do it)! When you're done, run /challenge/check, which will check things out and give the flag to you.


### Solve
**Flag:** `pwn.college{8EaZtYJuCrnDc-2uOHofgwZfbH3.0VOxEzNxwSNyMzNzEzW}`

The challenge requires us to move the file `/flag` into `/tmp/hack-the-planet`. We can do so using the `mv` command. After moving the file, run `/challenge/check` to retrieve the flag.

```
mv /flag /tmp/hack-the-planet
Correct! Performing 'mv /flag /tmp/hack-the-planet'.
/challenge/check
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:
pwn.college{8EaZtYJuCrnDc-2uOHofgwZfbH3.0VOxEzNxwSNyMzNzEzW}
```

### New Learnings

`mv` is a command used to move files. The first argument is the source path and the second argument is the destination path. 

If source and destination are in the same directory, `mv` simply renames the file, since it doesn't need to be moved anywhere.

