---
id: ekucjwzvveiczxiyvz1gi8j
title: 3-Navigation
desc: ''
updated: 1684789339457
created: 1680489495900
---

```bash
pwd # Print name of current working directory
cd  # Change directory
ls  # List directory contents
```

# Understanding the file system tree

Like Windows, a Unix-like operating system such as Linux organizes its files in what is called a hierarchical directory structure. This means they are organized in a tree-like pattern of directories (sometimes called folders in other systems), which may contain files and other directories. The first directory in the file system is called the root directory. The root directory contains files and subdirectories, which contain more files and subdirectories, and so on.

Note that unlike Windows, which has a separate file system tree for each storage device, Unix-like systems such as Linux always have a single file system tree, regardless of how many drives or storage devices are attached to the computer. Storage devices are attached (or more correctly, mounted) at various points on the tree according to the whims of the system administrator, the person (or people) responsible for the maintenance of the system.

# The current working directory

When we first log in to our system (or start a terminal emulator session), our current working directory is set to our home directory. Each user account is given its own home directory, and it is the only place a regular user is allowed to write files.

# Changing the current working directory

## Absolute pathnames

An absolute pathname begins with the root directory and follows the tree branch by branch until the path to the desired directory or file is completed.

```bash
cd /usr/bin # Start with from the root directory (represented by the leading slash in the pathname)

[me@linuxbox bin]$ # The prompt has changed (now showing us the path that we are in)
```

## Relative pathnames

Where an absolute pathname starts from the root directory and leads to its destination, a relative pathname starts from the working directory. To do this, it uses a couple of special notations to represent relative positions in the file system tree. These special notations are "`.`" and "`..`".

The `.` notation refers to the working directory, and the `..` notation refers to the working directory’s parent directory.

In almost all cases, we can omit the `./` part because it is implied.

```bash
cd ./<folder name>
cd <folder name>
```

In general, if we do not specify a pathname to something, the working directory will be assumed.

> **Important facts about filenames**
>
> On Linux systems, files are named in a manner similar to that of other systems such as Windows, but there are some important differences.
>
> - Filenames that begin with a period character are hidden. This only means that ls will not list them unless you say `ls -a`. When your account was created, several hidden files were placed in your home directory to configure things for your account. In addition, some applications place their configuration and settings files in your home directory as hidden files.
> - Filenames and commands on Linux, like Unix, are case-sensitive. The filenames "File1" and "file1" refer to different files.
> - Though Linux supports long filenames that may contain embedded spaces and punctuation characters, limit the punctuation characters in the names of files you create to period, dash, and underscore. Most important, do not embed spaces in filenames. If you want to represent spaces between words in a filename, use underscore characters.
> - Linux has no concept of a “file extension” like some other operating systems. You may name files any way you like. The contents or purpose of a file is determined by other means. Although Unix-like operating systems don’t use file extensions to determine the contents/purpose of files, many application programs do.

# Some helpful shortcuts

```bash
cd              # Changes the working directory to your home directory
cd -            # Changes the working directory to the previous working directory.
cd ~<user_name> # Changes the working directory to the home directory of user_name
```