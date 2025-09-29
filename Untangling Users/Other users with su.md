# Untangling Users

## Other users with su
With no arguments, su will start a root shell (after authenticating with root's password). However, you can also give a username as an argument to switch to that user instead of root. For example:
```
hacker@dojo:~$ su some-user
Password:
some-user@dojo:~$
```
Awesome! In this level, you must switch to the zardus user and then run /challenge/run. Zardus' password is dont-hack-me. Good luck!

### Solve
**Flag:** `pwn.college{w4bH9r6CJZ9_F8qPwt7zdL-sna6.QX1UDN1wSNyMzNzEzW}`

To retrieve the flag, we need to change user  to `zardus` and then run `/challenge/run`. To switch user, we can use the `su` command.

```
su
Password:
root@users~becoming-root-with-su:/home/hacker# ls
/challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{4amGp-ygO2y18H6Ug6sDikUBbZZ.QX2UDN1wSNyMzNzEzW}
```
### New Learnings

`su` command can also be used to switch users, by providing username as argument.

