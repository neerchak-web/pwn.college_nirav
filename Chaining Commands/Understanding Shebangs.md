# Chaining Commands

## Understanding Shebangs
You're well on your way to your new life as a shell scripter! However, so far, your shellscripts can only be launched from the shell. Things worked great in the previous level (because you were invoking your script from the bash shell), but they won't work if your script was being invoked by, say, a program written in Python (or any other language).

When a program is invoked in Linux, the Linux kernel first inspects the file to determine how it should be run. This does NOT use the extension (which is why you don't have to name your shell scripts with a .sh extension, or your Python scripts with a .py extension, or so on). Rather, Linux looks at the first few bytes of the file for this information.

There are a bunch of different types of programs, but if the program file starts with the characters #! (often termed a "shebang"), Linux treats the file as an interpreted program, and the contents of the rest of the line as the path to the interpreter. It then invokes the interpreter with the path to the program file as its only argument.

Consider this shell script:

#!/bin/bash
```
echo "Hello Hackers!"
```
This can be executed as:
```
hacker@dojo:~$ chmod a+x script.sh
hacker@dojo:~$ ./script.sh
Hello Hackers!
hacker@dojo:~$
```
When ./script.sh was executed, Linux opened the file, read the first line, extracted /bin/bash as the interpreter, and executed /bin/bash ./script.sh to launch the script!

Note, the shebang line must be the VERY FIRST line of the file - no blank lines or spaces before it!

For this challenge, create a script at /home/hacker/solve.sh that has a proper shebang and outputs "hack the planet". Remember to make it executable, then run /challenge/run to verify your script works correctly!

FUN FACT: Common shebangs you might see:

#!/bin/bash for bash scripts
#!/usr/bin/python3 for Python scripts
#!/bin/sh for POSIX shell scripts --- this is a more primitive predecessor to bash with fewer features, but more compatibility to non-Linux systems!

### Solve
**Flag:** `pwn.college{cmJNmweokL4N6cf-X_hKOfjpqBo.0VOzMDOxwSNyMzNzEzW}`

```
printf '%s\n' '#!/bin/bash' "echo 'hack the planet'" > /home/hacker/solve.sh
chmod a+x /home/hacker/solve.sh
/challenge/run
Testing your script...
Perfect! Your flag:
Flag: pwn.college{cmJNmweokL4N6cf-X_hKOfjpqBo.0VOzMDOxwSNyMzNzEzW}
```
### New Learnings

When a program is invoked in Linux, the Linux does not identify the type of file it is from its extension. It observese the first few bits to understand how to interpret the program.

There are a bunch of different types of programs, but if the program file starts with the characters #! (often termed a "shebang"), Linux treats the file as an interpreted program, and the contents of the rest of the line as the path to the interpreter. It then invokes the interpreter with the path to the program file as its only argument.