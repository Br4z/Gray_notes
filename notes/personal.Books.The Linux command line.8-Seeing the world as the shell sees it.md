---
id: p88z6aqdw936rkrbtw1bw1i
title: 8-Seeing the world as the shell sees it
desc: ''
updated: 1684883898411
created: 1684786322897
---

```bash
echo # Display a line of text
```

# Expansion

With expansion, we enter something, and it is expanded into something else before the shell acts upon it.

```bash
echo this is a test

this is a test

# ---------------------------------- # ---------------------------------- #

echo *

Desktop Documents ls-output.txt Music Pictures Public Templates Videos
```

> The "*" character means match any character in a file name.

The simple answer to that behavior is that the shell expands the "*" into something else (in this instance, the name of the files in the current working directory) before the `echo` command is executed. When the `ENTER` key is pressed, the shell automatically expands any qualifying characters on the command line before the command is carried out, so the `echo` command never saw the "*", only its expanded result.

## Pathname

The mechanism by which wildcards work is called **pathname expansion**.

```bash
ls

Desktop ls-output.txt Pictures Templates
Documents Music Public Videos

# ---------------------------------- # ---------------------------------- #

echo D* # Directories starting with a "D"

Desktop Documents

# ---------------------------------- # ---------------------------------- #

echo *s # Directories ending with a "s"

Documents Pictures Templates Videos

# ---------------------------------- # ---------------------------------- #

echo [[:upper:]]* # Directories starting with a capital letter

Desktop Documents Music Pictures Public Templates Videos

# ---------------------------------- # ---------------------------------- #

echo /usr/*/share # Directories with have a /usr as a parent and a /share as a child

/usr/kerberos/share /usr/local/share
```

> **Pathname expansion of hidden files**
>
> ```bash
> echo .*      # Includes the `.` (actual) and `..` (parent) directories
>
> echo  .[!.]* # Now excludes the two directories mentioned in the command above
> ```
>
> The second command will exclude files (or directories) named with multiple leading periods. `ls -A` provide a correct listing of hidden files.

## Tilde

When used at the beginning of a word, it expands into the name of the home directory of the named user, if no user is named, the home directory of the current user.

```bash
echo ~

/home/me

# ---------------------------------- # ---------------------------------- #

echo ~foo

/home/foo
```

## Arithmetic

The shell allows arithmetic to be performed by expansion. This allows us to use the shell prompt as a calculator.

```bash
$((expression))

# ---------------------------------- # ---------------------------------- #

echo $((2 + 2))

4
```

> Arithmetic expansion supports only integers.

| Operator |                                           Description                                           |
|:--------:|:-----------------------------------------------------------------------------------------------:|
|   `+`    |                                            Addition                                             |
|   `-`    |                                           Subtraction                                           |
|   `*`    |                                         Multiplication                                          |
|   `/`    | Division (but remember, since expansion supports only integer arithmetic, results are integers) |
|   `%`    |                             Modulo, which simply means "remainder"                              |
|   `**`   |                                         Exponentiation                                          |

```bash
echo $(($((5 ** 2)) * 3)) # Is equal to $(((5 ** 2) * 3))

75

# ---------------------------------- # ---------------------------------- #

echo Five divided by two equals $((5 / 2))

Five divided by two equals 2

# ---------------------------------- # ---------------------------------- #

echo with $((5 % 2)) left over

with 1 left over
```

# Brace

With it, you can create multiple text string from a pattern containing braces.

```bash
echo Front-{A,B,C}-Back

Front-A-Back Front-B-Back Front-C-Back
```

Patterns to be brace expanded may contain a leading portion called a **preamble** and a trailing portion called a **postscript**. The pattern may not contain unquoted withespace.

```bash
echo Number_{1..5}

Number_1 Number_2 Number_3 Number_4 Number_5

# ---------------------------------- # ---------------------------------- #

echo {01..15}

01 02 03 04 05 06 07 08 09 10 11 12 13 14 15

# ---------------------------------- # ---------------------------------- #

echo {Z..A}

Z Y X W V U T S R Q P O N M L K J I H G F E D C B A

# ---------------------------------- # ---------------------------------- #

echo a{A{1,2},B{3,4}}b

aA1b aA2b aB3b aB4b

# ---------------------------------- # ---------------------------------- #

mkdir Photos
cd Photos
mkdir {2007..2009}-{01..12}
ls

2007-01 2007-07 2008-01 2008-07 2009-01 2009-07
2007-02 2007-08 2008-02 2008-08 2009-02 2009-08
2007-03 2007-09 2008-03 2008-09 2009-03 2009-09
2007-04 2007-10 2008-04 2008-10 2009-04 2009-10
2007-05 2007-11 2008-05 2008-11 2009-05 2009-11
2007-06 2007-12 2008-06 2008-12 2009-06 2009-12
```

# Parameter

Many of its capabilities have to do with the system's ability to store small chunks of data and to give each chunk a name. Many such chunks, more properly called variables, are available for your examination.

```bash
echo $USER

me

# ---------------------------------- # ---------------------------------- #

printev | less # To see a list of variables
```

# Command