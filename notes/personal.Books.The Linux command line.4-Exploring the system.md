---
id: utea9yv49m2umusqurvte3i
title: 4-Exploring the system
desc: ''
updated: 1684789284903
created: 1680491611722
---

```bash
ls   # List directory contents
file # Determinate file type
less # View file contents
```

# More fun with ls

The `ls` command is probably the most used command, and for good reason. With it, we can see directory contents and determine a variety of important file and directory attributes.

```bash
ls <path>
ls <path> <path> # We can even specify multiple directories
ls -l            # We changed the output to the long format.
```

## Options and arguments

This brings us to a very important point about how most commands work. Commands are often followed by one or more **options** that modify their behavior and, further, by one or more **arguments**.

```bash
command -options arguments
ls -lt           # Show the long format and sort it by modification time
ls -lt -reverse  # Reverse the order of the sort
```

> Command options, like filenames on Linux, are case-sensitive.


| Option |   Long option    |                                                                                                          Description                                                                                                          |
|--------|------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| -a     | --all            | List all files, even those with names that begin with a period, which are normally not listed (that is, hidden).                                                                                                              |
| -A     | --almost-all     | Like the -a option, except it does not list . (current directory) and .. (parent directory).                                                                                                                                  |
| -d     | --directory      | Ordinarily, if a directory is specified, ls will list the contents of the directory, not the directory itself. Use this option in conjunction with the -l option to see details about the directory rather than its contents. |
| -F     | --classify       | This option will append an indicator character to the end of each listed name. For example, it will append a forward slash (/) if the name is a directory.                                                                    |
| -h     | --human-readable | In long format listings, display file sizes in humanreadable format rather than in bytes.                                                                                                                                     |
| -l     |                  | Display results in long format.                                                                                                                                                                                               |
| -r     | --reverse        | Display the results in reverse order. Normally, ls displays its results in ascending alphabetical order.                                                                                                                      |
| -S     |                  | Sort results by file size.                                                                                                                                                                                                    |
| -t     |                  | Sort by modification time.                                                                                                                                                                                                    |


## A longer look at long format

As we saw earlier, the `-l` option causes ls to display its results in long format. This format contains a great deal of useful information. Here is an example from an Ubuntu system:

```bash
-rw-r--r-- 1 root root 32059 2017-04-03 11:05 oo-cd-cover.odf
```

|      Field       |                                                                                                                                                                      Meaning                                                                                                                                                                       |
|------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| -rw-r-r--        | Access rights to the file. The first character indicates the type of file. Among the different types, a leading dash means a regular file, while a `d` indicates a directory. The next three characters are the access rights for the file's owner, the next three are for members of the file's group, and the final three are for everyone else. |
| 1                | File's number of hard links.                                                                                                                                                                                                                                                                                                                       |
| root             | The username of the file's owner.                                                                                                                                                                                                                                                                                                                  |
| root             | The name of the group that owns the file.                                                                                                                                                                                                                                                                                                          |
| 32059            | Size of the file in bytes.                                                                                                                                                                                                                                                                                                                         |
| 2017-04-03 11:05 | Date and time of the file's last modification.                                                                                                                                                                                                                                                                                                     |
| oo-cd-cover.odf  | Name of the file.                                                                                                                                                                                                                                                                                                                                  |

## Determining a File's Type with file

```bash
file <file path> # Will print a brief description of the file's contents

# ---------------------------------- # ---------------------------------- #

file picture.jpg

picture.jpg: JPEG image data, JFIF standard 1.01
```

There are many kinds of files. In fact, one of the common ideas in Unixlike operating systems such as Linux is that "everything is a file".

## Viewing File Contents with less

The `less` command is a program to view text files.

> **What is "text"?**
>
> There are many ways to represent information on a computer. All methods involve defining a relationship between the information and some numbers that will be used to represent it. Computers, after all, understand only numbers, and all data is converted to numeric representation.
>
> Some of these representation systems are very complex (such as compressed video files), while others are rather simple. One of the earliest and simplest is called ASCII text. ASCII (pronounced "as-key") is short for American Standard Code for Information Interchange. This is a simple encoding scheme that was first used on Teletype machines to map keyboard characters to numbers.
>
> Text is a simple one-to-one mapping of characters to numbers. It is very
> compact. Fifty characters of text translates to fifty bytes of data. Plain ASCII text files contain only the characters themselves and a few rudimentary control codes such as tabs, carriage returns, and line feeds.
>

Once started, the less program allows us to scroll forward and backward through a text file.

|      Command       |                          Action                           |
|:------------------:|-----------------------------------------------------------|
| PAGE UP or b       | Scroll back one page.                                     |
| PAGE DOWN or space | Scroll forward one page.                                  |
| Up arrow           | Scroll up one line.                                       |
| Down arrow         | Scroll down one line.                                     |
| G                  | Move to the end of the text file.                         |
| 1G or g            | Move to the beginning of the text file.                   |
| /characters        | Search forward to the next occurrence of characters.      |
| n                  | Search for to the next occurrence of the previous search. |
| h                  | Display help screen.                                      |
| q                  | Quit less.                                                |

> **Less is more**
>
>
> The less program was designed as an improved replacement of an earlier Unix program called more. The name less is a play on the phrase "less is more"—*a motto of modernist architects and designers.*
>
> less falls into the class of programs called pagers, programs that allow the easy viewing of long text documents in a page-by-page manner. Whereas the more program could only page forward, the less program allows paging both forward and backward and has many other features as well.
>

### Taking a Guided Tour

The file system layout on a Linux system is much like that found on other Unix-like systems. The design is actually specified in a published standard called the **Linux** **Filesystem** **Hierarchy** Standard. Not all Linux distributions conform to the standard exactly, but most come pretty close.

> **Remember** **the** **Copy** **and** **Paste** **Trick!**
>
>
> If you are using a mouse, you can double-click a filename to copy it and middle-click to paste it into commands.
>

|    Directory     |                                                                                                                                                                                                                                      Description                                                                                                                                                                                                                                       |
|:----------------:|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `/`              | The root directory, where everything begins.                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `/bin`           | Contains binaries (programs) that must be present for the system to boot and run.                                                                                                                                                                                                                                                                                                                                                                                                      |
| `/boot`          | Contains the Linux kernel, initial RAM disk image (for drivers needed at boot time), and the boot loader. Interesting files include `/boot/grub/grub.conf`, or `menu.lst`, which is used to configure the boot loader, and `/boot/vmlinuz` (or something similar), the Linux kernel.                                                                                                                                                                                                   |
| `/dev`           | This is a special directory that contains device nodes. "Everything is a file" also applies to devices. Here is where the kernel maintains a list of all the devices it understands.                                                                                                                                                                                                                                                                                                   |
| `/etc`           | Contains all the system-wide configuration files. It also contains a collection of shell scripts that start each of the system services at boot time. Everything in this directory should be readable text. While everything in `/etc` is interesting, here are some all-time favorites: `/etc/crontab`, a file that defines when automated jobs will run; `/etc/fstab`, a table of storage devices and their associated mount points; and `/etc/passwd`, a list of the user accounts. |
| `/home`          | In normal configurations, each user is given a directory in /home. Ordinary users can write files only in their home directories. This limitation protects the system from errant user activity.                                                                                                                                                                                                                                                                                       |
| `/lib`           | Contains shared library files used by the core system programs. These are similar to dynamic link libraries (DLLs) in Windows.                                                                                                                                                                                                                                                                                                                                                         |
| `/lost+found`    | Each formatted partition or device using a Linux file system, such as ext3, will have this directory. It is used in the case of a partial recovery from a file system corruption event. Unless something really bad has happened to your system, this directory will remain empty                                                                                                                                                                                                      |
| `/media`         | On modern Linux systems, the `/media` directory will contain the mount points for removable media such as USB drives, CD-ROMs, and so on, that are mounted automatically at insertion.                                                                                                                                                                                                                                                                                                 |
| `/mnt`           | On older Linux systems, the `/mnt` directory contains mount points for removable devices that have been mounted manually.                                                                                                                                                                                                                                                                                                                                                              |
| `/opt`           | Is used to install "optional" software. This is mainly used to hold commercial software products that might be installed on the system.                                                                                                                                                                                                                                                                                                                                                |
| `/proc`          | It's not a real file system in the sense of files stored on your hard drive. Rather, it is a virtual file system maintained by the Linux kernel. The "files" it contains are peepholes into the kernel itself. The files are readable and will give you a picture of how the kernel sees your computer.                                                                                                                                                                                |
| `/root`          | This is the home directory for the root account.                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `/sbin`          | This directory contains "system" binaries. These are programs that perform vital system tasks that are generally reserved for the superuser.                                                                                                                                                                                                                                                                                                                                           |
| `/tmp`           | Is intended for the storage of temporary, transient files created by various programs. Some configurations cause this directory to be emptied each time the system is rebooted.                                                                                                                                                                                                                                                                                                        |
| `/usr`           | Is likely the largest one on a Linux system. It contains all the programs and support files used by regular users.                                                                                                                                                                                                                                                                                                                                                                     |
| `/usr/bin`       | Contains the executable programs installed by your Linux distribution. It is not uncommon for this directory to hold thousands of programs.                                                                                                                                                                                                                                                                                                                                            |
| `/usr/lib`       | The shared libraries for the programs in `/usr/bin`.                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `/usr/local`     | is where programs that are not included with your distribution but are intended for system-wide use are installed. Programs compiled from source code are normally installed in `/usr/local/bin`. On a newly installed Linux system, this tree exists, but it will be empty until the system administrator puts something in it.                                                                                                                                                       |
| `/usr/sbin`      | Contains more system administration programs.                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `/usr/share`     | contains all the shared data used by programs in `/usr/bin`. This includes things such as default configuration files, icons, screen backgrounds, sound files, and so on.                                                                                                                                                                                                                                                                                                              |
| `/usr/share/doc` | Most packages installed on the system will include some kind of documentation. In `/usr/share/doc`, we will find documentation files organized by package.                                                                                                                                                                                                                                                                                                                             |
| `/var`           | With the exception of `/tmp` and `/home`, the directories we have looked at so far remain relatively static; that is, their contents don't change. The `/var` directory tree is where data that is likely to change is stored. Various databases, spool files, user mail, and so forth, are located here.                                                                                                                                                                              |
| `/var/log`       | Contains log files, records of various system activity. These are important and should be monitored from time to time. The most useful ones are `/var/log/messages` and `/var/log/syslog`. Note that for security reasons on some systems, you must be the superuser to view log files.                                                                                                                                                                                                |

## Symbolic Links

```bash
lrwxrwxrwx 1 root root 11 2018-08-11 07:34 libc.so.6 -> libc-2.6.so
```

Notice how the first letter of the listing is l and the entry seems to have two filenames? This is a special kind of a file called a symbolic link (also known as a soft link or symlink). In most Unix-like systems, it is possible to have a file referenced by multiple names.

## Hard Links

Hard links also allow files to have multiple names, but they do it in a different way.

## Summing Up

One thing you should take away from this is how open the system is. In Linux there are many important files that are plain human-readable text. Unlike many proprietary systems, Linux makes everything available for examination and study.