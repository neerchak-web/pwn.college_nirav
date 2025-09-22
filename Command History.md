# Hello Hackers

## Command History
You're going to type a lot of commands, and typing everything from scratch can be annoying. Luckily, the shell saves a history of every command you invoke.

You can scroll through those saved commands with the up/down arrow keys, and we'll practice that in this challenge. This challenge will inject the flag into your history. Bring up a terminal, hit the up arrow, and grab it! In other challenges, the history will contain the log of the commands you've run, so if you need to run a similar command again, you can use the arrow keys to scroll through and find it!



### Solve
**Flag:** `pwn.college{ATvrpjZKFLqivyXzwSvxqjUxay_.0lNzEzNxwSNyMzNzEzW}`

The flag is injected into the shell history when the terminal session starts. By using the up-arrow key, we can access previous "commands" and get the flag.



### New Learnings
All previously entered commands are stored in the shell's history during a session. The up and down arrow keys can be used to navigate between previously inputted commands.
