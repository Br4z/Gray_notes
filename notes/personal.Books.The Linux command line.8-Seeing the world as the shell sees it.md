---
id: p88z6aqdw936rkrbtw1bw1i
title: 8-Seeing the world as the shell sees it
desc: ''
updated: 1685212172460
created: 1684786322897
---

```bash
echo # Display a line of text
```

## Expansion

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

### Pathname

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

### Tilde

When used at the beginning of a word, it expands into the name of the home directory of the named user, if no user is named, the home directory of the current user.

```bash
echo ~

/home/me

# ---------------------------------- # ---------------------------------- #

echo ~foo

/home/foo
```

### Arithmetic

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

### Brace

With it, you can create multiple text string from a pattern containing braces.

```bash
echo Front-{A,B,C}-Back

Front-A-Back Front-B-Back Front-C-Back
```

Patterns to be brace expanded may contain a leading portion called a **preamble** and a trailing portion called a **postscript**. The pattern may not contain unquoted whitespace.

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

### Parameter

Many of its capabilities have to do with the system's ability to store small chunks of data and to give each chunk a name. Many such chunks, more properly called variables, are available for your examination.

```bash
echo $USER

me

# ---------------------------------- # ---------------------------------- #

printev | less # To see a list of variables
```

### Command

Allows us to use the output of a command as an expansion.

```bash
echo $(ls)

Desktop Documents ls-output.txt Music Pictures Public Templates Videos

# ---------------------------------- # ---------------------------------- #

ls -l $(which cp)

-rwxr-xr-x 1 root root 71516 2007-12-05 08:58 /bin/cp
```

We are no limited to just simple commands. Entire pipelines can be used.

```bash
file $(ls -d /usr/bin/* | greq zip)

/usr/bin/bunzip2: symbolic link to `bzip2'
/usr/bin/bzip2: ELF 32-bit LSB executable, Intel 80386, version 1
(SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.9, stripped
/usr/bin/bzip2recover: ELF 32-bit LSB executable, Intel 80386, version 1
(SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.9, stripped
/usr/bin/funzip: ELF 32-bit LSB executable, Intel 80386, version 1
(SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.9, stripped
/usr/bin/gpg-zip: Bourne shell script text executable
/usr/bin/gunzip: symbolic link to `../../bin/gunzip'
/usr/bin/gzip: symbolic link to `../../bin/gzip'
/usr/bin/mzip: symbolic link to `mtools'
```

## Quoting

Now that we've seen how many ways the shell can perform expansions, it's time to learn how we can control it.

```bash
echo this is a      test # word splitting by the shell removed extra whitespace

this is a test

# ---------------------------------- # ---------------------------------- #

echo The total is $100.00 # parameter expansion substituted an empty string for the value of $1 because it was an undefined variable

The total is 00.00
```

The shell provides a mechanism called **quoting** to selectively suppress unwanted expansions.

### Double quotes

If we place text inside double quotes, all the special characters used by the shell lose their special meaning and are treated as ordinary characters. The exceptions are:

- `$` (dollar sign).
- `\` (backslash).
- `\`` (backtick).

```bash
ls -l two words.txt

ls: cannot access two: No such file or directory
ls: cannot access words.txt: No such file or directory

# ---------------------------------- # ---------------------------------- #

ls -l "two words.txt"

-rw-rw-r-- 1 me me 18 2018-02-20 13:03 two words.txt
```

---

By default, word splitting looks for the presence of spaces, tabs, and newlines (line feed characters) and treats them as **delimiters** between words.

```bash
echo "this is a      test"

this is a      test

# ---------------------------------- # ---------------------------------- #

echo $(cal)

February 2020 Su Mo Tu We Th Fr Sa 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17
18 19 20 21 22 23 24 25 26 27 28 29

echo "$(cal)" # Well display calendar
```

### Single quotes

If we need to suppress **all** expansions, we use single quotes.

```bash
echo text ~/*.txt {a,b} $(echo foo) $((2+2)) $USER

text /home/me/ls-output.txt a b foo 4 me

# ---------------------------------- # ---------------------------------- #

echo "text ~/*.txt {a,b} $(echo foo) $((2+2)) $USER"

text ~/*.txt {a,b} foo 4 me

# ---------------------------------- # ---------------------------------- #

echo 'text ~/*.txt {a,b} $(echo foo) $((2+2)) $USER

text ~/*.txt {a,b} $(echo foo) $((2+2)) $USER
```

### Escaping Characters

To **escape a character** we can precede that character with a backslash.

```bash
echo "The balance for user $USER is: \$5.00"
```

It is possible to use characters in filenames that normally have special meaning to the shell. These would include $, !, &, spaces, and others. To include a special character in a filename, we can do this:

```bash
mv bas\&filename good_filename
```

> Within single quotes, the backslash loses its special meaning and is treated as an ordinary character.

### Backslash escape sequences

In addition to its role as the escape character, the backslash is used as part of a notation to represent certain special characters called **control codes**.

| Escape sequence |                         Meaning                          |
|:---------------:|:--------------------------------------------------------:|
|      `\a`       |     Bell (an alert that causes the computer to beep)     |
|      `\b`       |                        Backspace                         |
|      `\n`       | Newline; on Unix-like systems, this produces a line feed |
|      `\r`       |                     Carriage return                      |
|      `\t`       |                           Tab                            |

Adding the `-e` option to echo will enable interpretation of escape sequences. You can also place them inside `$' '`.

```bash
sleep 10; echo -e "Time's up\a"

sleep 10; echo "Time's up" $'\a'
```
