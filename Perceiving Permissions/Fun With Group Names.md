# Perceiving Permissions

## Fun With Group Names
In the previous levels, you may have noticed that your hacker user is a member of the hacker group, and that zardus is a member of the zardus group. There is a convention in Linux that every user has their own group, but this does not have to be the case. For example, many computer labs will put all of their users into a single, shared users group.

The point is, you've used hacker for the group before, but in this level, that is not going to work. I'll still allow you to use chgrp, but I have randomized the name of the group that your user is in. You will need to use the id command to figure that name out, then chgrp to victory!


### Solve
**Flag:** `pwn.college{g9b02neTNlRgDPsl_qlD7wQmAok.QXycjM1wSNyMzNzEzW}`

In this level we will be allowed to use `chgrp` without root access. We can use `chgrp` to change the group ownership of `/flag` to the current user's group. We can use `id` to find the group name.

```
id
uid=1000(hacker) gid=1000(grp10550) groups=1000(grp10550)
chgrp grp10550 /flag
cat /flag
pwn.college{g9b02neTNlRgDPsl_qlD7wQmAok.QXycjM1wSNyMzNzEzW}
```
### New Learnings

`chown` command is used to change group ownership of files. The first argument is the new group, and the second is the file address.
