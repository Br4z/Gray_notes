---
id: tvmme18939tpggywggtaceu
title: 6-Working with commands
desc: ''
updated: 1684789872098
created: 1680926055609
---

```bash
type    # Indicate how a command name is interpreted
which   # Display which executable program will be executed
help    # Get help for shell builtins
man     # Display a command's manual page
apropos # Display a list of appropriate commands

info    # Display a command's info entry
whatis  # Display one-line manual page descriptions
alias   # Create an alias for a command
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

    # ---------------------------------- # ---------------------------------- #

    type type

    type is a shell builtin

    # ---------------------------------- # ---------------------------------- #

    type ls

    ls is aliased to `ls --color=tty'

    # ---------------------------------- # ---------------------------------- #

    type cp

    cp is /bin/cp
    ```

- `which`

    Is used to determine the exact location of a given executable.

    ```bash
    which ls

    /bin/ls
    ```

    `which` works only for executable programs, not builtins or aliases that are substitutes for actual executable programs.

    ```bash
    which cd

    /usr/bin/which: no cd in (/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games)
    ```

    > This result is a fancy way of saying "command not found".

# Getting a command's documentation

## `help`: get help for shell builtins.

```bash
help <command>

# ---------------------------------- # ---------------------------------- #

help cd

cd: cd [-L|[-P [-e]] [-@]] [dir]...
```

> When square brackets appear in the description of a command's syntax, they indicate optional items. A vertical bar character indicates mutually exclusive items.

## `--help`: display usage information.

Many executable programs support a `--help` option that displays a description of the command's supported syntax and options.

```bash
<command> --help

# ---------------------------------- # ---------------------------------- #

mkdir --help

Usage: mkdir [OPTION] DIRECTORY...
Create the DIRECTORY(ies), if they do not already exist. ...
```

## `man`: display a program's manual page.

Most executable programs intended for command line use provide a formal piece of documentation called a manual or man page. A special paging program called man is used to view them.

```bash
man <command>
```

Man pages vary somewhat in format, but generally contain the following:

- Title (the page's name)
- Synopsis of the command's syntax
- Description of the command's purpose
- Listing and description of each of the command's options

> On most Linux systems, man uses less to display the manual page.


The "manual" that man displays is broken into sections and covers not only user commands:



| Section | Contents                                       |
|:-------:|------------------------------------------------|
|    1    | User commands                                  |
|    2    | Programming interfaces for kernel system calls |
|    3    | Programming interfaces to the C library        |
|    4    | Special files such as device nodes and drivers |
|    5    | File formats                                   |
|    6    | Games and amusements such as screen savers     |
|    7    | Miscellaneous                                  |
|    8    | System administration commands                 |

> Sometimes we need to refer to a specific section of the manual to find what we are looking for.

## `apropos`: display appropriate commands.

It is also possible to search the list of man pages for possible matches based on a search term.

```bash
apropos <term>

# ---------------------------------- # ---------------------------------- #

apropos partition

addpart (8) - tell the kernel about the existence of a partition...
```

The first field in each line of output is the name of the man page, and the second field shows the section.

> The `man` command with the `-k` option performs the same function as `apropos`.

## `whatis`: Display one-line manual page descriptions.

Displays the name and a one-line description of a `man` page matching a specified keyword.

> **The most brutal man page of them all**
>
> As we have seen, the manual pages supplied with Linux and other Unix-like systems are intended as reference documentation and not as tutorials. Many man pages are hard to read, but I think the grand prize for difficulty has got to go to the man page for bash. As I was doing research for this book, I gave the bash man page careful review to ensure that I was covering most of its topics. When printed, it's more than 80 pages long and extremely dense, and its structure makes absolutely no sense to a new user.
>
> On the other hand, it is very accurate and concise, as well as being extremely complete.

## `info`: display a program's info entry.

The GNU Project provides an alternative to man pages for their programs, called info. Info manuals are displayed with a reader program named **info**.

> Info pages are **hyperlinked** much like web pages.

The info program reads info files, which are tree structured into individual **nodes**, each containing a single topic. Info files contain hyperlinks that can move you from node to node. A hyperlink can be identified by its leading asterisk and is activated by placing the cursor upon it and pressing `ENTER`.

```bash
info <command>
```

|          Command          | Action                                                                  |
|:-------------------------:|-------------------------------------------------------------------------|
|            `?`            | Display command help                                                    |
| `PAGE UP` or `BACKSPACE`  | Display previous page                                                   |
| `PAGE DOWN` or `SPACEBAR` | Display next page                                                       |
|        `n` (next)         | Display the next node                                                   |
|      `p` (previous)       | Display the previous node                                               |
|         `u` (up)          | Display the parent node of the currently displayed node, usually a menu |
|          `ENTER`          | Follow the hyperlink at the cursor location                             |
|            `q`            | Quit                                                                    |

> Most of the command line programs we have discussed so far are part of the GNU Project's coreutils package.

## README and other program documentation files

Many software packages installed on your system have documentation files residing in the `/usr/share/doc` directory.

# Creating our own commands with alias

It's possible to put more than one command on a line by separating each command with a semicolon:

```bash
command1; command2; command3

cd /usr; ls; cd -
```

1. Name availability verification.

    ```bash
    type test

    test is a shell builtin

    # ---------------------------------- # ---------------------------------- #

    type foo

    bash: type: foo: not found
    ```

2. Alias creation.

    ```bash
    alias <alias name>='<string>'

    # ---------------------------------- # ---------------------------------- #

    alias foo='cd /usr; ls; cd -'

    # ---------------------------------- # ---------------------------------- #

    type foo

    foo is aliased to `cd /usr; ls; cd -'
    ```

3. Alias removal.

    ```bash
    unalias foo

    # ---------------------------------- # ---------------------------------- #

    type foo

    bash: type: foo: not found
    ```

While we purposefully avoided naming our alias with an existing command name, it is not uncommon to do so. This is often done to apply a commonly desired option to each invocation of a common command.

```bash
type ls

ls is aliased to `ls --color=tty'

# ---------------------------------- # ---------------------------------- #

alias # Display all aliases defined in the environment
```

There is one tiny problem with defining aliases on the command line. They vanish when your shell session ends.