---
id: 45ii26woiux6823pehhnkvv
title: 12-The environment
desc: ''
updated: 1686359788607
created: 1686277045346
---

```BASH
printenv # Print part or all of the environment
set      # Set shell options
export   # Export environment to subsequently executed programs
alias    # Create an alias for a command
```

## What is stored in the environment?

The shell stores two basic types of data in the environmente. They are **environment variables** and **shell variables**.

### Examining the environment

The `set` command will show both the **shell** and **environment** variables, while `printenv` will display only the latter.

```BASH
printenv | less # See all environment variable through less

# printenv <environment variable> See the content of a environment variable

set | less # Display both the shell and environment variables, as well as any defined shell functions.

#echo $<environment variable>  See the content of a environment variable
```

> One element of the environment that neither `set` nor `printenv` displays is aliases (but you can see them with `alias` command).

## How is the environment established?

When we log on to the system, the bash program starts and reads a series
of configuration scripts called **startup files**, which define the default environment shared by all users.

### What's in a startup file?

```BASH
# .bash_profile
# Get the aliases and functions
if [ -f ~/.bashrc ]; then
		. ~/.bashrc
fi
# User specific environment and startup programs
PATH=$PATH:$HOME/bin
export PATH
```

The first conditional is call an if **compound command**, an can be translate into:

```
If the file "~/.bashrc" exists, then
		read the "~/.bashrc" file.
```

The `export` command tells the shell to make the contents of `PATH` available to child processes of this shell.
