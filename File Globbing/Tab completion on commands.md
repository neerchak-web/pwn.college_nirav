# File Globbing

## Tab completion on commands
Tab completion is for more than files! You can also tab-complete commands. This level has a command that starts with pwncollege, and it'll give you the flag. Type pwncollege and hit the tab key to auto-complete it!

NOTE: You can auto-complete any command, but be careful: callous auto-completes without double-checking the result can wreak havoc in your shell if you accidentally run the wrong commands!


### Solve
**Flag:** `pwn.college{4ssEQGzxOzma8EJwSR1d9SMvRx9.0VN0EzNxwSNyMzNzEzW}`

To retrieve the flag, we need to run a command that starts with `pwncollege`. To auto-expand it to the required command, we can use tab completion.

Doing so expands the original command to `pwncollege-8582`. Running it gives us the flag.

```
pwncollege-8582 
Correct! Here is your flag:
pwn.college{4ssEQGzxOzma8EJwSR1d9SMvRx9.0VN0EzNxwSNyMzNzEzW}
```

### New Learnings

Tab completion can also be used for commands.