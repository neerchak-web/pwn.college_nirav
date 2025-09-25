# Digesting Documentation

## Searching Manuals
You can scroll man pages with the arrow keys (and PgUp/PgDn) and search with /. After searching, you can hit n to go to the next result and N to go to the previous result. Instead of /, you can use ? to search backwards!

Find the option that will give you the flag by reading the challenge man page. The manual containts multiple arguments, out of which one will dipslay the flag when invoked.

### Solve
**Flag:** `pwn.college{QZ8ORzVkqZ3kvmKBqYmWcdeiOAm.QX1EDO0wSNyMzNzEzW}`

The manual of the program `challenge` can be displayed using the `man` command. The manual containts multiple arguments, out of which one will dipslay the flag when invoked.

We can search for the pattern "flag" in the manual by hitting `/` and typing it in. We can toggle through the results by hitting `n`.

As seen in the manual, when `--nrnezp` is given as argument to the program `/challenge/challenge`, the required flag is printed.

```
man challenge

gzip: stdout: Broken pipe
/challenge/challenge --nrnezp
Initializing...
Correct usage! Your flag: pwn.college{QZ8ORzVkqZ3kvmKBqYmWcdeiOAm.QX1EDO0wSNyMzNzEzW}
```

### New Learnings

We can search for patterns in a manual by hitting `/` and entering the pattern to be searched. To go to the next result, hit `n` and to go to the previous result, hit `N`. To search backwards, hit `?` instead of `/`.

