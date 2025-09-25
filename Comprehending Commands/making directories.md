# Comprehending Commands

## making directories
We can create files. How about directories? You make directories using the mkdir command. Then you can stick files in there!

Watch:
```
hacker@dojo:~$ cd /tmp
hacker@dojo:/tmp$ ls
hacker@dojo:/tmp$ ls
hacker@dojo:/tmp$ mkdir my_directory
hacker@dojo:/tmp$ ls
my_directory
hacker@dojo:/tmp$ cd my_directory
hacker@dojo:/tmp/my_directory$ touch my_file
hacker@dojo:/tmp/my_directory$ ls
my_file
hacker@dojo:/tmp/my_directory$ ls /tmp/my_directory/my_file
/tmp/my_directory/my_file
hacker@dojo:/tmp/my_directory$
```
Now, go forth and create a /tmp/pwn directory and make a college file in it! Then run /challenge/run, which will check your solution and give you the flag!


### Solve
**Flag:** `pwn.college{QpYPwUHNonjF3HsVKvDXHBOcHqh.QXxMDO0wSNyMzNzEzW}`

First, we change our working directory to `/tmp` using `cd`. Then, we can create a new directory `pwn` in `/tmp` using the `mkdir` command. 

After making the directory, we can create a new file `college` in `/tmp/pwn` using the `touch` command. 

Run `/challenge/run` after creating the file to retrieve the flag.

```
cd /tmp
mkdir pwn
cd /tmp/pwn
touch college
/challenge/run
Success! Here is your flag:
pwn.college{QpYPwUHNonjF3HsVKvDXHBOcHqh.QXxMDO0wSNyMzNzEzW}
```

### New Learnings

`mkdir` is a command used to create new directories. It takes the path of the directory to be created as its argument.

