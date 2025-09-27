# Data Manipulation

## Sorting data
Files (or output lines of commands) aren't always in the order you need them! The sort command helps you organize data. It reads lines from input (or files) and outputs them in sorted order:
```
hacker@dojo:~$ cat names.txt
  hack
  the
  planet
  with
  pwn
  college
hacker@dojo:~$ sort names.txt
  college
  hack
  planet
  pwn
  the
  with
hacker@dojo:~$
```
By default, sort orders lines alphabetically. Arguments can change this:

-r: reverse order (Z to A)
-n: numeric sort (for numbers)
-u: unique lines only (remove duplicates)
-R: random order!
In this challenge, there's a file at /challenge/flags.txt containing 100 fake flags, with the real flag mixed among them. When sorted alphabetically, the real flag will be at the end (we made sure of this when generating fake flags). Go get it!

### Solve
**Flag:** `pwn.college{kzuhadkB_PDrD9c8Mb_QvADpvX0.0FM0MDOxwSNyMzNzEzW}`

`/challenge/flags.txt` contains 100 fake flags, of which the alphabetically last flag is the required flag.

To extract the required flag from the file, we can sort the lines of the flag in reverse alphabetical order using `sort -r`, and print the first sorted line using `head -n 1`.

```
sort -r /challenge/flags.txt | head -n 1
pwn.college{kzuhadkB_PDrD9c8Mb_QvADpvX0.0FM0MDOxwSNyMzNzEzW}
```
### New Learnings

`sort` is a command used to output lines from the input in sorted order. `sort` can take input from files and stdin. By default, sort orders lines alphabetically. Arguments can change this:

-r: reverse order (Z to A)
-n: numeric sort (for numbers)
-u: unique lines only (remove duplicates)
-R: random order


