---
id: 3wteziy120nbzkpr80vrxyk
title: 7-Redirection
desc: ''
updated: 1684790089753
created: 1683928108898
---

```bash
cat  # Concatenate files
sort # Sort lines of text
uniq # Report or omit repeated lines
grep # Print lines matching a pattern
wc   # Print newline, word, and byte counts for each files
head # Output the fir part of a files
tail # Output the last part of a file
tee  # Read from standard input and write to standard output files
```

# Standard input, output, and error

Keeping with the Unix theme of "everything is a file", programs such as **ls** actually send their results to a special file called **standard output** (often expressed as **stdout**) and their status messages to another file called **standard error** (**stderr**). By default, both standard output and standard error are linked to the screen and not saved into a disk file.

# Redirecting standard output

I/O redirection allows us to redefine where standard output goes. To redirect standard output to another file instead of the screen, we use the `>` redirection operator followed by the name of the file.

```bash
<command> > <existing file>

ls -l /usr/bin > ls-output.txt
```

With the command above we created a long listing of the `/usr/bin` directory and sent the
results to the file `ls-output.txt`. Let's set what happened if we wire an wrong directory:

```bash
ls -l /bin/usr > ls-output.txt

ls: cannot access /bin/usr: No such file or directory
```

The reason why it displays an error message instead of saving it to the file is because the **ls** program does not send its error messages to standard output.Instead, like most well-written Unix programs, it sends its error messages to standard error. Because we redirected only standard output and not standard error, the error message was still sent to the screen.

```bash
ls -l ls-output.txt

-rw-rw-r-- 1 me me 0 2018-02-01 15:08 ls-output.txt
```

The file now has zero length, this is because when we redirect output with the `>` redirection operator, the destination file is always rewritten from the beginning. In fact, if we ever need to actually truncate a file (or create a new, empty file), we can use a trick like this:

```bash
> ls-output.txt
```

> Simply using the redirection operator with no command preceding it will truncate an existing file or create a new, empty file.

If we want to append redirected output to a file instead of overwriting the file from the beginning, we use the `>>` redirection operator.

```bash
<command> >> <existing file>

ls -l /usr/bin >> ls-output.txt
ls -l /usr/bin >> ls-output.txt
ls -l /usr/bin >> ls-output.txt

-rw-rw-r-- 1 me me 503634 2018-02-01 15:45 ls-output.txt
```

> We repeated the command three times, resulting in an output file three times as large.

# Redirecting standard error

```bash
0 # Standard input
1 # Output
2 # Error

<command> <file stream>> <existing file>

ls -l /bin/usr 2> ls-error.txt
```

## Redirecting standard output and standard error to one file

```bash
<command> > <existing file> 2>&1

ls -l /bin/usr > ls-output.txt 2>&1
```

Using this method, we perform two redirections. First we redirect standard output to the file `ls-output.txt`, and then we redirect file descriptor 2 (standard error) to file descriptor 1 (standard output) using the notation `2>&1`.

> Notice that the order of the redirections is significant
>
> The redirection of standard error must always occur after redirecting standard
output or it doesn’t work.

Recent versions of bash provide a second, more streamlined method for performing this combined redirection, shown here:

```bash
ls -l /bin/usr &> ls-output.txt

# ---------------------------------- # ---------------------------------- #

ls -l /bin/usr &>> ls-output.txt # You can also append
```

## Disposing of unwanted output

The system provides a way to do this by redirecting output to a special file called `/dev/null`. This file is a system device often referred to as a **bit bucket**, which accepts input and does nothing with it. To suppress error messages from a command, we do this:

```bash
ls -l /bin/usr 2> /dev/null
```

# Redirecting standard input

## `cat`

```bash
cat <file path>

cat ls-output.txt
```

Reads one or more files and copies them to standard output.

---

Because `cat` can accept more than one file as an argument, it can also be used to join files together.

```bash
movie.mpeg.001 movie.mpeg.002 ... movie.mpeg.099

cat movie.mpeg.0* > movie.mpeg
```

> Because wildcards always expand in sorted order, the arguments will bearranged in the correct order.

---

If we enter cat with no arguments, it reads from standard input, and since standard input is, by default, attached to the keyboard, it’s waiting for us to type something. If we typed something and press `CTRL + d` to tell cat that it has reached end of file (EOF) on standard input.

> We can use this behavior to create short text files.

---

Let’s try redirecting standard input.

```bash
cat < lazy_dog.txt

The quick brown fox jumped over the lazy dog.
```

## Pipelines

```bash
<command> | <command>

ls -l /usr/bin | less
```

The capability of commands to read data from standard input and send to standard output is utilized by a shell feature called **pipelines**. Using the **pipe** operator `|`, the standard output of one command can be piped into the standard input of another.

### Filters

```bash
<command> | <filters> | <command>
```

Filters take input, change it somehow, and then output it.

---

```bash
ls /bin /usr/bin | sort | less
```

The command above is to make a combined list of all the executable programs in `/bin` and `/usr/bin`, put them in sorted order, and view the resulting list.

> The diffence between `>` and `|`
>
> Redirection operator silently creates or overwrites files, so you need to treat it with a lot of respect.

#### `uniq`

Removes duplicate items from the list and is often used in conjunction with `sort` filter.

```bash
ls /bin /usr/bin | sort | uniq | less    # See the uniques elements

# ---------------------------------- # ---------------------------------- #

ls /bin /usr/bin | sort | uniq -d | less # See the duplicates elements
```

#### `wc`

```bash
wc ls-output.txt

7902 64566 503634 ls-output.txt
```

It prints: lines, words and bytes counting respectively. If we executed it without command line arguments, `wc` accepts standard input.

> The `-l` option limits its output to report only lines. Adding it to a pipeline is a handy way to count things.

```bash
ls /bin /usr/bin | sort | uniq | wc -l # See the number of items we have in our sorted list
```

#### `grep`

```bash
grep <pattern> <filename>
```

When `grep` encounters a "pattern" in the file, it prints out the lines containing it.

> The patterns that it can match can be very complex (with regular expressions).

```bash
ls /bin /usr/bin | sort | uniq | grep zip # Find all the files in our list of programs that had the word "zip" embedded in the name

bunzip2
bzip2
gunzip
gzip
unzip
zip
zipcloak
zipgrep
zipinfo
zipnote
zipsplit
```

There are a couple of handy options for `grep`:

- `-i`: perform the search in a no case sensitive way.
- `-v`: print only those lines that don't match the pattern.

#### `head` and `tail`

The `head` command prints the first 10 lines of a file, and the `tail` command prints the last 10 lines.

> The number of lines can be adjusted with the `-n` option.

```bash
head -n 5 ls-output.txt

total 343496
-rwxr-xr-x 1 root root 31316 2017-12-05 08:58 [
-rwxr-xr-x 1 root root 8240 2017-12-09 13:39 411toppm
-rwxr-xr-x 1 root root 111276 2017-11-26 14:27 a2p
-rwxr-xr-x 1 root root 25368 2016-10-06 20:16 a52dec

# ---------------------------------- # ---------------------------------- #

tail -n 5 ls-output.txt

-rwxr-xr-x 1 root root 5234 2017-06-27 10:56 znew
-rwxr-xr-x 1 root root 691 2015-09-10 04:21 zonetab2pot.py
-rw-r--r-- 1 root root 930 2017-11-01 12:23 zonetab2pot.pyc
-rw-r--r-- 1 root root 930 2017-11-01 12:23 zonetab2pot.pyo
lrwxrwxrwx 1 root root 6 2016-01-31 05:22 zsoelim -> soelim
```

These can be used in pipelines as well:

```bash
ls /usr/bin | tail -n 5

znew
zonetab2pot.py
zonetab2pot.pyc
zonetab2pot.pyo
zsoelim
```

`tail` has an option that allows you to view the file in real time (`-f`).

> That is incredible useful when you're monitoring log files.

```bash
tail -f /var/log/messages # Superuser privileges are required to perform this command

Feb 8 13:40:05 twin4 dhclient: DHCPACK from 192.168.1.1
Feb 8 13:40:05 twin4 dhclient: bound to 192.168.1.4 -- renewal in 1652 seconds.
Feb 8 13:55:32 twin4 mountd[3953]: /var/NFSv4/musicbox exported to both 192.168.1.0/24 and
twin7.localdomain in 192.168.1.0/24,twin7.localdomain
Feb 8 14:07:37 twin4 dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Feb 8 14:07:37 twin4 dhclient: DHCPACK from 192.168.1.1
Feb 8 14:07:37 twin4 dhclient: bound to 192.168.1.4 -- renewal in 1771 seconds.
Feb 8 14:09:56 twin4 smartd[3468]: Device: /dev/hda, SMART Prefailure Attribute: 8 Seek_Time_
Performance changed from 237 to 236
Feb 8 14:10:37 twin4 mountd[3953]: /var/NFSv4/musicbox exported to both 192.168.1.0/24 and
twin7.localdomain in 192.168.1.0/24,twin7.localdomain
Feb 8 14:25:07 twin4 sshd(pam_unix)[29234]: session opened for user me by (uid=0)
Feb 8 14:25:36 twin4 su(pam_unix)[29279]: session opened for user root by me(uid=500)
```

> The promp won't be available until you press `CTRL + c`.

#### `tea`

The `tea` program reads standard input and copies it to both standard output (allowing the data to continue down the pipeline) and to one or more files. This is useful for capturing a pipeline's contents at an intermediate stage of processing.

```bash
ls /usr/bin | tee ls.txt | grep zip

bunzip2
bzip2
gunzip
gzip
unzip
zip
zipcloak
zipgrep
zipinfo
zipnote
zipsplit
```