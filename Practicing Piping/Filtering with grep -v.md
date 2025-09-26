# Practicing Piping

## Filtering with grep -v
The grep command has a very useful option: -v (invert match). While normal grep shows lines that MATCH a pattern, grep -v shows lines that do NOT match a pattern:
```
hacker@dojo:~$ cat data.txt
hello hackers!
hello world!
hacker@dojo:~$ cat data.txt | grep -v world
hello hackers!
hacker@dojo:~$
```
Sometimes, the only way to filter to just the data you want is to filter out the data you don't want. In this challenge, /challenge/run will output the flag to stdout, but it will also output over 1000 decoy flags (containing the word DECOY somewhere in the flag) mixed in with the real flag. You'll need to filter out the decoys while keeping the real flag!

Use grep -v to filter out all the lines containing "DECOY" and reveal the real flag!


### Solve
**Flag:** `pwn.college{09SG2dTErIJJslpQ8SX1mkkXEWK.QX1ATO0wSNyMzNzEzW}`

Running the program `/challenge/run` gives us the required flag as output. However, it will be hidden among multiple fake flags. 

The challenge states that all fake flags contain the pattern "DECOY". We can filter out this pattern from the output using `grep -v`.

```
/challenge/run | grep -v DECOY
pwn.college{ExNg8XgdxY8ik2xyU1QiUfQjT4H.0FOxEzNxwSNyMzNzEzW}
```

### New Learnings

When `grep` is used with the flag `-v`, it will filter out entries which contain the pattern given as its argument. 