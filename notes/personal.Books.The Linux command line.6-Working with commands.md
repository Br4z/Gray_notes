---
id: tvmme18939tpggywggtaceu
title: 6-Working with commands
desc: ''
updated: 1681505857428
created: 1680926055609
---

```bash
type    -> Indicate how a command name is interpreted
which   -> Display which executable program will be executed
help    -> Get help for shell builtins
man     -> Display a command’s manual page
apropos -> Display a list of appropriate commands
info    -> Display a command’s info entry
whatis  -> Display one-line manual page descriptions
alias   -> Create an alias for a command
```

# What exactly are commands?

A command can be one of four different things.

- An executable program
- A command built into the shell itself

    > Like `cd` command.

- A shell function
- An alias

# Identifying commands

- `type`

    Shell builtin that displays the kind of command the shell will execute, given a particular command name.

    ```bash
    type <command>

    type type -> type is a shell builtin
    type ls   -> ls is aliased to `ls --color=tty'
    type cp   -> cp is /bin/cp
    ```

- `which`

    Is used to determine the exact location of a given executable.

    ```bash
    which ls -> /bin/ls
    ```

    `which` works only for executable programs, not builtins or aliases that are substitutes for actual executable programs.

    ```bash
    which cd -> /usr/bin/which: no cd in (/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games)
    ```

    > This result is a fancy way of saying "command not found".

