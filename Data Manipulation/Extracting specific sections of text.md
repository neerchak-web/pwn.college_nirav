# Data Manipulation

## Extracting specific sections of text
Sometimes, you want to grab specific columns of data, such as the first column, the third column, or the 42nd column. For this, there's the cut command.

For example, imagine that you have the following data file:
```
hacker@dojo:~$ cat scores.txt
hacker 78 99 67
root 92 43 89
hacker@dojo:~$
```
You could use cut to extract specific columns:
```
hacker@dojo:~$ cut -d " " -f 1 scores.txt
hacker
root
hacker@dojo:~$ cut -d " " -f 2 scores.txt
78
92
hacker@dojo:~$ cut -d " " -f 3 scores.txt
99
43
hacker@dojo:~$
```
The -d argument specifies the column delimiter (how columns are separated). In this case, it's a space character. Of course, it has to be in quotes here so that the shell knows that the space is an argument rather than a space separating other arguments! The -f argument specifies the field number (which column to extract).

In this challenge, the /challenge/run program will give you a bunch of lines with random numbers and single characters (characters of the flag) as columns. Use cut to extract the flag characters, then pipe them to tr -d "\n" (like the previous level!) to join them together into a single line. Your solution will look something like /challenge/run | cut ??? | tr ???, with the ??? filled out.


### Solve
**Flag:** `pwn.college{otrMT6U3Y4NgUUBsQQTAyCpEpfg.01NxEzNxwSNyMzNzEzW}`

By running `/challenge/run`, we see that it contains lines of text, where each line is a sequence of digits, followed by a blankspace and an alphabet. Clearly, the alphabets from each line together form the required flag.

We can consider the sequence of digits and the alphabets as two columns separated by a blankspace. 

We can extract the alphabet column (column 2) from `/challenge/run` using `cut -d`. We can get all the alphabets in one line by removing the newline characters from the alphabet column using `tr -d`.

```
/challenge/run
17763 p
28732 w
6636 n
27574 .
10115 c
18894 o
8339 l
10245 l
7781 e
13725 g
31991 e
32002 {
12468 o
9079 t
2749 r
7880 M
1144 T
25699 6
22297 U
13156 3
6253 Y
19487 4
8983 N
22825 g
11111 U
11280 U
32748 B
3011 s
19894 Q
31908 Q
32051 T
17625 A
2577 y
1093 C
24115 p
7289 E
2469 p
19281 f
19219 g
407 .
2895 0
5181 1
12515 N
8598 x
5928 E
121 z
15157 N
11425 x
9851 w
1601 S
20724 N
801 y
31581 M
15070 z
25783 N
12786 z
13779 E
27594 z
21821 W
13009 }
/challenge/run | cut -d " " -f 2| tr -d "\n"
pwn.college{otrMT6U3Y4NgUUBsQQTAyCpEpfg.01NxEzNxwSNyMzNzEzW}
```
### New Learnings

`cut` is a command used to extract sections from lines of text. `cut` can take input from files and stdin.

One of the ways to use `cut` is to extract columns from a data file. This can be done by using the `-d` flag, followed by the `-f` flag.

The `-d` flag takes the column separating character/s as its argument. The `-f` flag takes the column number to be extracted as its argument.