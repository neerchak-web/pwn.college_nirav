# Comprehending Commands

## grepping for a needle in a haystack
Sometimes, the files that you might cat out are too big. Luckily, we have the grep command to search for the contents we need! We'll learn it in this challenge.

There are many ways to grep, and we'll learn one way here:
```
hacker@dojo:~$ grep SEARCH_STRING /path/to/file
```
Invoked like this, grep will search the file for lines of text containing SEARCH_STRING and print them to the console.

In this challenge, I've put a hundred thousand lines of text into the /challenge/data.txt file. grep it for the flag!

HINT: The flag always starts with the text pwn.college.




### Solve
**Flag:** `pwn.college{Yy6dNj6kASASUEyNERj3APeqOBH.QX3EDO0wSNyMzNzEzW}`

The absolute path to a text file which contains the flag is given in the challenge. Since all flags contain the substring "pwn.college", we can use the `grep` command with the first argument as `pwn.college` and the second argument as the absolute path to the file to retrieve the flag.

```
grep pwn.college /challenge/data.txt
pwn.college{Yy6dNj6kASASUEyNERj3APeqOBH.QX3EDO0wSNyMzNzEzW}
```

### New Learnings
`grep` is a command used to search for patterns (substrings) in files. One of the ways to use `grep` is to specify the first argument as the search pattern, and the subsequent arguments as all the file paths to search in.

This is particularly useful for searching for specific patterns in large files.

