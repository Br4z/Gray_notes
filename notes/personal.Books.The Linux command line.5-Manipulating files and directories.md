---
id: nvz60210ewd6nfwxwnfst0w
title: 5-Manipulating files and directories
desc: ''
updated: 1686277467576
created: 1680558212222
---

- `mkdir`  create directories

	```BASH
	mkdir dir1 dir2 dir3 # would create three directories named dir1, dir2, and dir3
	```

## Wildcards

(also known as **globbing**) allows you to select filenames based on patterns of characters.

| Wildcard        | Meaning                                                          |
|:---------------:|------------------------------------------------------------------|
| `*`             | Matches any characters                                           |
| `?`             | Matches any single character                                     |
| `[characters]`  | Matches any character that is a member of the set characters     |
| `[!characters]` | Matches any character that is not a member of the set characters |
| `[[:class:\]]`  | Matches any character that is a member of the specified class    |

| Character class | Meaning                            |
|:---------------:|------------------------------------|
| `[:alnum:]`     | Matches any alphanumeric character |
| `[:alpha:]`     | Matches any alphabetic character.  |
| `[:digit:]`     | Matches any numeral                |
| `[:lower:]`     | Matches any lowercase letter       |
| `[:upper:]`     | Matches any uppercase letter       |

> **Wildcards work in the GUI, too**
>
> Wildcards are especially valuable not only because they are used so frequently on the command line but because they are also supported by some graphical file managers.
> **Characters ranges**
>
> These are traditional Unix notations and worked in older versions of Linux as well. They can still work, but you have to be careful with them because they will not produce the expected results unless properly configured.

## `cp` (copy files and directories)

```BASH
cp item1 item2           # Copies the single file or directory item1 to the file or directory item2
# cp item... <directory> # Copies multiple items (either files or directories) into a directory
```

### Useful options (`cp`)

|        Option         |                                                                                                                                    Meaning                                                                                                                                    |
|-----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-a`, `--archive`     | Copy the files and directories and all of their attributes, including ownerships and permissions. Normally, copies take on the default attributes of the user performing the copy                                                                                             |
| `-i`, `--interactive` | Before overwriting an existing file, prompt the user for confirmation. **If this option is not specified, cp will silently (meaning there will be no warning) overwrite files**.                                                                                              |
| `-r`, `--recursive`   | Recursively copy directories and their contents. This option (or the `-a` option) is required when copying directories.                                                                                                                                                       |
| `-u`, `--update`      | When copying files from one directory to another, only copy files that either don't exist or are newer than the existing corresponding files in the destination directory. This is useful when copying large numbers of files as it skips files that don't need to be copied. |
| `-v`, `--verbose`     | Display informative messages as the copy is performed.                                                                                                                                                                                                                        |

## `mv`  (move/rename files and directories)

```BASH
mv item1 item2           # To move or rename the file or directory item1 to item2
# mv item... <directory> # To move one or more items from one directory to another.
```

### Useful options (`mv`)

|        Option        |                                                                                     Meaning                                                                                     |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-i`, `--interactive` | Before overwriting an existing file, prompt the user for confirmation. **If this option is not specified, cp will silently (meaning there will be no warning) overwrite files**. |
| `-u`, `--update`      | When moving files from one directory to another, only move files that either don't exist or are newer than the existing corresponding files in the destination directory.        |
| `-v`, `--verbose`     | Display informative messages as the copy is performed.                                                                                                                           |

## `rm` (remove files and directories)

### Useful options (`rm`)

| Option                | Meaning                                                                                                                                                                 |
|-----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-i`, `--interactive` | Before deleting an existing file, prompt the user for confirmation. **If this option is not specified, rm will silently delete files**.                                 |
| `-r`, `--recursive`   | Recursively delete directories. This means that if a directory being deleted has subdirectories, delete them too. To delete a directory, this option must be specified. |
| `-f`, `--force`       | Ignore nonexistent files and do not prompt. This overrides the `--interactive` option.                                                                                  |
| `-v`, `--verbose`     | Display informative messages as the deletion is performed.                                                                                                              |

> **Be carefully with `rm`!**
>
> Unix-like operating systems such as Linux do not have an undelete command. Once you delete something with rm, it's gone. Linux assumes you're smart and you know what you're doing.
>
> Be particularly careful with wildcards. Here is a useful tip: whenever you use wildcards with `rm` (besides carefully checking your typing!), test the wildcard first with `ls`.

## `ln` (create links)

```BASH
# ln <file> <link>    Creates a hard link
# ln -s <item> <link> Creates a symbolic link (where item is either a file or a directory)
```

### Hard links

Hard links are the original Unix way of creating links, compared to symbolic links, which are more modern. By default, every file has a single hard link that gives the file its name. When we create a hard link, we create an additional directory entry for a file. Hard links have two important limitations.

- A hard link cannot reference a file outside its own file system. This means a link cannot reference a file that is not on the same disk partition as the link itself.

- A hard link may not reference a directory.

A hard link is indistinguishable from the file itself. Unlike a symbolic link, when you list a directory containing a hard link, you will see no special indication of the link. When a hard link is deleted, the link is removed, but the contents of the file itself continue to exist (that is, its space is not deallocated) until all links to the file are deleted. It is important to be aware of hard links because you might encounter them from time to time, but modern practice prefers symbolic links.

### Symbolic links

Symbolic links were created to overcome the limitations of hard links. They work by creating a special type of file that contains a text pointer to the referenced file or directory. In this regard, they operate in much the same way as a Windows shortcut, though of course they predate the Windows feature by many years.

A file pointed to by a symbolic link and the symbolic link itself are largely indistinguishable from one another.

## Building a playground

### Creating hard links

When thinking about hard links, it is helpful to imagine that files are made up of two parts.

- The data part containing the file's contents

- The name part that holds the file's name

When we create hard links, we are actually creating additional name parts that all refer to the same data part. The system assigns a chain of disk blocks to what is called an **inode**, which is then associated with the name part. Each hard link therefore refers to a specific inode containing the file's contents.

> The `ls` command has a way to reveal this information. It is invoked with the `-i` option (in this version of the listing, the first field is the inode number).

### Creating symbolic links

Notice, that the length of the symbolic link file is the number of characters in the string to the file which it is pointing (**path**).

```BASH
# ln -s <file path> <symbolic link path>
```

> The `<file path>`, can be a relative (of the symbolic link path) or absolute path.

In most cases, using relative pathnames is more desirable because it allows a directory tree containing symbolic links and their referenced files to be renamed and/or moved without breaking the links.

When we create a symbolic link, we are creating a text description of where the target file is relative to the symbolic link.

### Removing files and directories

Most Linux distributions configure ls to display broken links. The presence of a broken link is not in and of itself dangerous, but it is rather messy. If we try to use a broken link, we will see `No such file or directory` error.

One thing to remember about symbolic links is that most file operations are carried out on the link's target, not the link itself. rm is an exception. When you delete a link, it is the link that is deleted, not the target.
