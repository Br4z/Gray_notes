---
id: 4c2flfxt8g8ctoqxpemfixd
title: 10-Permissions
desc: ''
updated: 1686014298083
created: 1685645571550
---

```BASH
id     # Display user identity
chmod  # Change a file's mode
umask  # Set the  default file permissions
su     # Run a shell as another user
sudo   # Execute a command as another user
chown  # Change a file's owner
chgrp  # Change a file's group ownership
passwd # Change a user's password
```

## Owners, group Members, and everybody else

In the Unix security model, a user may own files and directories. When a user **owns** a file or directory, the user has control over its access. Users can, in turn, belong to a group consisting of one or more users who are given access to files and directories by their owners. In addition to granting access to a group, an owner may also grant some set of access rights to everybody, which in Unix terms is referred to as the **world**. To find out information about your identity, use the `id` command.

```BASH
id

uid=500(me) gid=500(me) groups=500(me)
```

When user accounts are created, users are assigned a number called a **user ID (uid)**, which is then, for the sake of the humans, mapped to a username. The user is assigned a **group ID (gid)** and may belong to additional groups.

---

User accounts are defined in the `/etc/passwd` file, and groups are defined in the `/etc/group` file. When user accounts and groups are created, these files are modified along with `/etc/shadow`, which holds information about the user's password. For each user account, the `/etc/passwd` file defines the:

- user (login) name.
- uid.
- gid.
- account's real name.
- home directory.
- login shell.

## Reading, writing, and executing

Access rights to files and directories are defined in terms of read access, write access, and execution access.

```BASH
> foo.txt
ls -l foo.txt

-rw-rw-r-- 1 me me 0 2018-03-06 14:52 foo.txt
```

The first of these characteres is the **file type**, the following table describes the mostly common ones to see:

| Attribute |                                                                                               File type                                                                                                |
|:---------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|    `-`    |                                                                                             A regular file                                                                                             |
|    `d`    |                                                                                              A directory                                                                                               |
|    `l`    | A symbolic link. Notice that with symbolic links, the remaining file attributes are always rwxrwxrwx and are dummy values. The real file attributes are those of the file the symbolic link points to. |
|    `c`    |                                 A character special file. This file type refers to a device that handles data as a stream of bytes, such as a terminal or `/dev/null`.                                 |
|    `b`    |                                        A block special file. This file type refers to a device that handles data in blocks, such as a hard drive or DVD drive.                                         |

The remaining nine characters of the file attributes, called the file mode, represent the read, write, and execute permissions for the file's owner, the file's group owner, and everybody else.

| Attribute |                                                                                               File                                                                                               | Directories                                                                                               |
|:---------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:----------------------------------------------------------------------------------------------------------|
|    `r`    |                                                                               Allows a file to be opened and read.                                                                               | Allows a directory’s contents to be listed if the execute attribute is also set.                          |
|    `w`    | Allows a file to be written to or truncated; however, this attribute does not allow files to be renamed or deleted. The ability to delete or rename files is determined by directory attributes. | Allows files within a directory to be created, deleted, and renamed if the execute attribute is also set. |
|    `x`    |                                    Allows a file to be treated as a
program and executed. Program files written in scripting languages must also be set as readable to be executed.                                    | Allows a directory to be entered |

### `chmod`

It's used to change the mode (permissions) of a file or directory, use the `chmod` command.

> For obvious reasons, only the file's owener or the superuser can do this.

The command supports two distinct ways of specifying mode changes:

- Octal number representation.
- Symbolic representation.

---

| Octal | Binary | File mode |
|:-----:|:------:|:---------:|
|   0   |  000   |   `---`   |
|   1   |  001   |   `--x`   |
|   2   |  010   |   `-w-`   |
|   3   |  011   |   `-wx`   |
|   4   |  100   |   `r--`   |
|   5   |  101   |   `r-x`   |
|   6   |  110   |   `rw-`   |
|   7   |  111   |   `rwx`   |

By using three octal digits, we can set the file mode for the owner, group owner, and world. ---

```BASH
chmod 600 foo.txt
ls -l foo.txt

-rw------- 1 me me 0 2018-03-06 14:52 foo.txt
```

---

Symbolic notation is divided into three parts:

- Who the change will affect.
- Which operation will be performed.
- What permission will be set.

| Symbol |                           Meaning                            |
|:------:|:------------------------------------------------------------:|
|  `u`   |   Short for "user" but means the file or directory owner.    |
|  `g`   |                         Group owner.                         |
|  `o`   |             Short for "others" but means world.              |
|  `a`   | Short for "all". This is a combination of `u`, `g`, and `o`. |

If no character is specified, "all" will be assumed.  The operation may be `a+` indicating that a permission is to be added, `a-` indicating that a permission is to be taken away, or `a=` indicating that only the specified permissions are to be applied and that all others are to be removed.

```BASH
chmod u+x,go=rw <file> # Add execute permission for the owner and set the permissions for the group and others to read and execute
```

> Symbolic notation does offer the advantage of allowing you to set a single attribute without disturbing any of the others (in octal you must specify all permissions).

### `umask`

```BASH
umask

022 # rw- for owner, r-- for group and r-- for world
```

As its name says, it works as a mask over the  `rw- rw- rw-` permissions, the explanation of the command above is:

|                    |  Permissions  |
|:------------------:|:-------------:|
| Original file mode | `rw- rw- rw-` |
|        Mask        | `000 010 010` |
|       Result       | `rw- r-- r--` |

The representation of the original file mode in binary is `110 110 110`. A AND operation was performed between Original file mode and NOT mask (wildcard), that is:

$$
\begin{array}{ccc}
      &110 &110 &110 \\
      &111 &101 &101 \\
    = &110 &100 &100
\end{array}
$$

according to the final permissions.

> In the explanation, the special permissions were omitted.

### Some special permissions

In addition to read, write, and execute permissions, there are some other, less used, permissions settings.

- setuid bit (octal 4000): when applied to an executable file, it changes the _effective user ID_ from that of the real user (the user actually running the program) to that of the program's owner.

    - This is useful when the executable file needs access to files or directories (or both) that a normal user would normally be prohibited from accessing.

    - Because this raises security concerns, the number of setuid programs must be held to an absolute minimum.

- setgid bit (octal 2000): changes the _effective group ID_ from the real group ID of the real user to that of the file owner.

    - If the setgid bit is set on a directory, newly created files in the directory will be given the group ownership of the directory rather of the group ownership of the file's creator.

    - This is useful in a shared directory when members of a common group need access to all the files in the directory, regardless of the file owner's primary group.

- sticky bit (octal 1000): This is a holdover from ancient Unix, where it was possible to mark an executable file as "not swappable".

    - Linux ignores the sticky bit, but if applied to a directory, it prevents users from deleting or renaming files unless the user is either the owner of the directory, the owner of the file, or the superuser.

        > This is often used to control access to a shared directory, such as `/tmp`.

```BASH
chmod u+s <file> # Assigning setuid to a file (-rwsr-xr-x)

chmod g+s <directory> # Assigning setgid to a directory (drwxrwsr-x)

chmod +t <directory> # Assigning the sticky bit to a directory (drwxrwxrwt)
```

## Changing identities

There are three ways to take on an alternate identity.

- Log out and log back in as the alternate user.
- Use the `su` command.
- Use the `sudo` command.

### `su`: run a shell with substitute user and groups IDs

The `su` command is used to start a shell as another user.

```BASH
su [-[l]] <user?>
```

- If the `-l` option is included, the resulting shell session is a login shell for the specified user. This means the user's environment is loaded, and the working directory is changed to the user’s home directory.

    > The `-l` may be abbreviated as `-`.

- If the user is not specified, the superuser is assumed.

It is also possible to execute a single command rather than starting a
new interactive command.

```BASH
su -c '<comman>' <user?>

# ---------------------------------- # ---------------------------------- #

su -c 'ls -l /root/*'

Password:
-rw------- 1 root root     754 2007-08-11 03:19 /root/anaconda-ks.cfg
/root/Mail:
total 0
```

### `sudo`: execute a command as another user

The administrator can configure sudo to allow an ordinary user to execute commands as a different user (usually the superuser) in a controlled way. The use of sudo does not require access to the superuser's password. Authenticating using sudo requires the user's own password.

One important difference between `su` and `sudo` is that `sudo` does not start a new shell, nor does it load another user's environment. This means that commands do not need to be quoted any differently than they would be without using `sudo`.

```BASH
sudo -i # Start an interactive superuser session (much like su -)

# ---------------------------------- # ---------------------------------- #

sudo -l # See what privileges are granted by sudo (in the current user)

User brandon may run the following commands on gray59:
    (ALL : ALL) ALL
```

### `chown`: change file owner and group

The `chown` command is used to change the owner and group owner of a file or directory.

```BASH
chown [owner][:[group]] <file>
```

| Argument  |                                                        Result                                                         |
|:---------:|:---------------------------------------------------------------------------------------------------------------------:|
| `:admins` |                       Changes the group owner to the group admins. The file owner is unchanged.                       |
|  `bob:`   | Changes the file owner from the current owner to user bob and changes the group owner to the login group of user bob. |

## Exercising our privileges

Imagine two users (bill and karen) that want to share all their music files between each other. For that purpose, Bill executed the following commands.

> Imagine a music group was created and has billy and karen as its members and Bill has access to superuser privileges via `sudo`.

```BASH
sudo mkdir /usr/local/share/Music

# ---------------------------------- # ---------------------------------- #

ls -ld /usr/local/share/Music

drwxr-xr-x 2 root root 4096 2018-03-21 18:05 /usr/local/share/Music

# ---------------------------------- # ---------------------------------- #

sudo chown :music /usr/local/share/Music
sudo chmod 775 /usr/local/share/Music
ls -ld /usr/local/share/Music

drwxrwxr-x 2 root music 4096 2018-03-21 18:05 /usr/local/share/Music
```

To this point, the directory has the right permissions, but we still have a problem (really two). With the current permissions, files and directories created within the Music directory will have the normal permissions of the users bill and karen.

```BASH
> /usr/local/share/Music/test_file
ls -l /usr/local/share/Music

-rw-r--r-- 1 bill   bill   0 2018-03-24 20:03 test_file
```

- The default umask on this system is 0022, which prevents group members from writing files belonging to other members of the group.

    > This would not be a problem if the shared directory contained only files, but because members of the group will need the ability to create files and directories inside directories created by other members it is.

- Each file and directory created by one member will be set to the primary group of the user rather than the group music.

```BASH
sudo chmod g+s /usr/local/share/Music
ls -ld /usr/local/share/Music

drwxrwsr-x 2 root music 4096 2018-03-24 20:03 /usr/local/share/Music

# ---------------------------------- # ---------------------------------- #

umask 0002
> /usr/local/share/Music/test_file # After have been removed the previous one
mkdir /usr/local/share/Music/test_dir
ls -l /usr/local/share/Music

drwxrwsr-x 2 bill   music 4096 2018-03-24 20:24 test_dir
-rw-rw-r-- 1 bill   music    0 2018-03-24 20:22 test_file
```

The one remaining issue is umask. The necessary setting lasts only until the end of session and must be reset.
