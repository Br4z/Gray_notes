---
id: dnsu5lwa6hq4b97g35s6acc
title: 1-Temario
desc: ''
updated: 1707878235221
created: 1706290903606
---

## 1 - Comandos básicos de Linux

- `id [OPTION]... [USER]...`: print user and group information for each specified USER, or (when USER omitted) for the current process.

- `grep [OPTION...] PATTERNS [FILE...]`: grep searches for `PATTERNS` in each FILE. `PATTERNS` is one or more patterns separated by newline characters, and grep prints each line that matches a pattern.

- `/etc/groups`: defines the groups in the system. There is one entry per line, with the following format:

	```BASH
	group_name:password:GID:user_list
	```

	The fields are as follows:

	- `group_name`: the name of the group.

	- `password`: the (encrypted) group password. If this field is empty, no password is needed.

	- `GID`: the numeric group ID.

	- `user_list`: a list of the usernames that are members of this group, separated by commas.

	> These days, many people run some version of the shadow password suite, where `/etc/passwd` has an `x` in the password field, and the encrypted passwords are in `/etc/shadow`, which is readable by the superuser only.

## 2 - Comandos básicos de Linux

- `/etc/passwd`: describes user login accounts for the system. Each line of the file describes a single user, and contains seven colon-separated fields:

	```BASH
	name:password:UID:GID:GECOS:directory:shell
	```

	The fields are as follows:

	- `name`: the user's login name. It should not contain capital letters.

	- `GID`: the numeric primary group ID for this user.

		> Additional groups for the user are defined in the system group file (`/etc/groups`).

	- `GECOS` (General Electric Comprehensive Operating System): is optional and used only for informational purposes.

		> Usually, it contains the full username.

	- `directory`: the user's home directory (the initial directory where the user is placed after logging in).

		> this field is used to set the `HOME`.

	- `shell`: program to run at login (if empty, use `/bin/sh`).

		> If set to a nonexistent executable, the user will be unable to login through login.

		> The value in this field is used to set the `SHELL` environment variable.

- `/etc/shells`: is a text file that contains the full pathnames of valid login shells.

## 3 - Control del flujo stderr-stdout, operadores y procesos en segundo plano

- `/etc/hots`: is a simple text file that associates IP addresses with hostnames, one line per IP address. For each host, a single line should be present with the following information:

	```BASH
	IP_address canonical_hostname [aliases...]
	```

- `command; ...; command`: is used to separate multiple commands on the same line.

- `command && ... && command`: execute the command that follows it only if the previous command completes successfully.

- `command || ... || command`: execute the command that follows it only if the previous command fails.

- `/dev/null`: data written to this file is discarded.

	> It is used as a **data sink**.

### Environment variables

Often referred to as ENVs, are dynamic values that wield significant influence over the behavior of programs and processes in the Linux operating system.

- `$?`: is used to store the exit status of the last command executed in a shell script or a terminal. The exit status is a number between $0$ and $255$ that indicates whether the command was completed successfully or failed.

	> A value of 0 means success, while any other value means failure.

### Bash Redirections

Are a way of manipulating the input and output of commands in a shell script or a terminal. By default, a command takes input from the keyboard and outputs it to the screen, but redirections allow you to change the source and destination of the data.

- `cmd > file`: redirects the standard output (stdout) of `cmd` to `file`.

- `cmd &> file`: redirects stdout and stderr of `cmd` to `file`.

- `cmd > file 2>&1`: another way to redirect both stdout and stderr of `cmd` to `file`.

	> `> file` redirects stdout to `file`, and `2>&1` redirects stderr to the same place where stdout is going, which is `file` in this case.

- `cmd &`: run a command in the background.

- `disown`: is used to remove jobs from the job table or keep them running even after you close the terminal window.

## 4 - Descriptores de archivo

are used to represent open files, sockets, pipes, and other input and output streams. A file descriptor is a non-negative integer value that serves as a unique identifier for a file or input/output channel that a process has opened.

- `exec [command [argument...]]`: shall open, close, and/or copy file descriptors as specified by any redirections as part of the command.

	> If `exec` is specified with command, it shall replace the shell with command without creating a new process. If arguments are specified, they shall be arguments to the command.

	Examples:

	- `exec 3<> file`: open `file` as file descriptor `3` for reading and writing.

		> To write to this file, we can use `... >&3`.

	- `exec 4[<>]&3`: make file descriptor `4` a copy of file descriptor `3`.

	- `exec 3[<>]&-`: close file descriptor `3`.

	- `exec 4[<>]&3-`: make file descriptor `4` a copy of file descriptor `3` and close file descriptor `3`.

## 5 - Lectura e interpretación de permisos

By executing `ls -l`, we can list the files using a long list format, which will show us the security of the files or directories. An example of this is:

```BASH
drwxr-xr-x 2 Brandon Brandon 4096 Jan 27 15:01 temp
```

Separating it into columns:

1. First.

	1. First character.

		- `-`: means it is a file.

		- `d`: means it is a directory.

	2. The next nine characters.

		- (`xxxxxxxxx`): show the security.

2. Second: number of hard links to the file or directory.

3. Third: owner of the file.

4. Fourth: group owner of the file.

5. Fifth: size of the file in bytes.

6. Sixth: the date and time the file was last modified.

7. Seventh: name of the file or the directory.

### What are the three permission groups in Linux?

```
---     ---     ---
rwx     rwx     rwx
user    group   other
```

### What are the three kinds of file permissions in Linux?

- `r` (read).

- `w` (write).

- `x` (execute).

	> In directories, it allows the user to enter the directory, and access files and directories inside.

### Operators and options

- `+`: add permissions.

- `-`: remove permissions.

- `=` set the permissions to the specified values.

---

- `u` (user): applies only to the owner of the file or directory.

- `g` (group): applies only to the group that has been assigned to the file or directory.

- `o` (other): applies to all other users on the system.

- `a` (all): all three (owner, groups, others).

## 7 - Asignación de permisos

To change the security permissions on files, we use `chmod`, which stands for "change mode", because the nine security characters are collectively called the security mode of the file.

- `chmod [OPTION]...`: change file mode bits.

	- `MODE[,MODE]... FILE...`.

	- `OCTAL-MODE FILE...`.

	- `--reference=RFILE FILE...`.

- `chgrp [OPTION]...`: change group ownership.

	- `GROUP FILE...`.

	- `--reference=RFILE FILE...`.

- `chown [OPTION]...`: change file owner and group.

	- `[OWNER][:[GROUP]] FILE...`.

	- `--reference=RFILE FILE...`.

- `useradd`: create a new user or update the default new user information.

	- `[options] LOGIN`.

	- `-D`.

	- `-D [options]`

- `groupadd [OPTIONS] NEWGROUP`: create a new group.

- `usermod [options] LOGIN`: modify a user account.

---

- `chmod ug+rw,o-x file.txt`: adds read (`r`) and write (`w`) permission to both user (`u`) and group (`g`) and revokes execute (`x`) permission from others (`o`) for the file `file.txt`.

- `chgrp new_group file.txt`: change the `file.txt` group to the `new_group` group.

- `useradd -m test`: create a user called "test" (with his respectively group) and create his home directory.

## 9 - Notación octal de permisos

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

Using the octal notations table instead of `r`, `w`, and `x`. Each digit octal notation can be used for either of the group `u`, `g`, or `o`. Executing `chmod ugo+rwx file.txt` is equal to `chmod 777 file.txt`.

## 10 - Permisos especiales – Sticky Bit, 11 - Control de atributos de ficheros en Linux – Chattr y Lsattr y 12 - Permisos especiales – SUID y SGID

### The setuid bit

This bit is present for files that have executable permissions. The setuid bit simply indicates that when running the executable, it will set its permissions to those of the user who created it (the owner), instead of setting them to the user who launched it. Similarly, there is a setgid bit that does the same for the gid.

To locate the setuid, look for an `s` instead of an `x` in the executable bit of the file permissions in the owner permission group.

- Set the setuid bit: `chmod u+s <file>` or `chmod 4--- <file>`.

- Remove the setuid bit: `chmod u-s <file>` or `chmod --- <file>`.

### The setgid bit

This bit affects both files and directories. When used on a file, it executes with the privileges of the group of the user who owns it, instead of executing with those of the group of the user who executed it. When the bit is set for a directory, the set of files in that directory will have the same group as the group of the parent directory, and not that of the user who created those files.

- Set the setgid bit: `chmod g+s <file>` or `chmod 2--- <file>`.

- Remove the setgid bit: `chmod g-s <file>` or `chmod --- <file>`.

### The sticky bit

When a directory has the sticky bit set, its files can be deleted or renamed only by the file owner, the directory owner and the root user.

- Set the sticky bit: `chmod +t <file>` or `chmod 1--- <file>`.

- Remove the sticky bit: `chmod -t <file>` or `chmod --- <file>`.

## 13 - Capabilities (privilegios especiales)

For the purpose of performing permission checks, traditional UNIX implementations distinguish two categories of processes: privileged processes (whose effective user ID is $0$, referred to as superuser or root), and unprivileged processes (whose effective UID is nonzero). Starting with Linux 2.2, Linux divides the privileges traditionally associated with the superuser into distinct units, known as **capabilities**, which can be independently enabled and disabled.

---

There are 5 options for a capability:

1. Permitted.

2. Inheritable.

3. Effective.

4. Bounding.

5. Ambient.

Only the first three can be assigned to executable files.

---

There are a lot of capabilities, but the most interesting two are:

- `CAP_SETUID`: make arbitrary manipulations of process UIDs.

- `CAP_SETGID`: make arbitrary manipulations of process GIDs.

---

- `getcap [-v] [-n] [-r] [-h] filename [...]`: displays the name and capabilities of each specified file.

- `setcap [-q] [-n <rootuid>] [-v] {capabilities|-|-r} filename [... capabilitiesN fileN]`: in the absence of the `-v` (verify) option, setcap sets the capabilities of each specified filename to the capabilities specified.

Examples of usage:

- `getcap -r / 2> /dev/null`: search for files that have capabilities in the entire system.

- `setcap -r file`: remove all the capabilities assigned to `file`.

- `setcap "all+pe cap_chown-pe" file`: add all capabilities in the Permitted and Effective sets of an executable, except for the `CAP_CHOWN` capability.

## 14 - Estructura de directorios del sistema

In Linux/Unix operating system, everything is a file; even directories are files, files are files, and devices like mouse, keyboard, printer, etc. are also files.

### Types of files in the Linux system

- General files.

- Directory files.

- Devices files.

![Linux directory structure](./assets/Courses/Introducción%20a%20Linux/1-1_Linux_directory_structure.png)

The Linux/Unix file system hierarchy base begins at the root, and everything starts with the root directory.

| Directories |                                                          Description                                                          |
|:-----------:|:-----------------------------------------------------------------------------------------------------------------------------:|
|    `/bin`     |                                                Binary or executable programs.                                                 |
|    `/etc`     |                                                  System configuration files.                                                  |
|    `/home`    |                                     Home directory. It is the default current directory.                                      |
|    `/opt`     |                                               Optional or third-party software.                                               |
|    `/tmp`     |                                         Temporary space, typically cleared on reboot.                                         |
|    `/usr`     |                                                    User-related programs.                                                     |
|    `/var`     |                                                          Log files.                                                           |
|    `/boot`    |                     Contains all the boot-related information files and folders such as conf, grub, etc.                      |
|    `/dev`     |                                   Location of device files such as dev/sda1, dev/sda2, etc.                                   |
|    `/lib`     |                                         Contains kernel modules and a shared library.                                         |
| `/lost+found` |                                        Used to find recovered bits of corrupted files.                                        |
|   `/media`    |                              Contains subdirectories where removable media devices are inserted.                              |
|    `/mnt`     |                              Contains temporary mount directories for mounting the file system.                               |
|    `/proc`    |       A virtual and pseudo-file system containing information about running processes with specific process IDs (PIDs).       |
|    `/run`     |                                                 Stores volatile runtime data.                                                 |
|    `/sbin`    |                                       Binary executable programs for an administrator.                                        |
|    `/srv`     |                                      Contains server-specific and server-related files.                                       |
|    `/sys`     | A virtual file system for modern Linux distributions to store and allows modification of the devices connected to the system. |

## 18 - Búsquedas a nivel de sistema

- `find [-H] [-L] [-P] [-D debugopts] [-Olevel] [starting-point...] [expression]`: search for files in a directory hierarchy.

	Some interesting options are:

	- `-type c`: File is of type "c".

		- `f`: regular file.

		- `d`: directory.

	- `-name pattern`: base of file name (the path with the leading directories removed) matches shell pattern "pattern".

		> `-iname pattern` like `-name`, but the match is case insensitive.

	- `-perm mode`: file's permission bits are exactly "mode".

	- `-group gname`: File belongs to group "gname".

		> numeric group ID allowed.

	- `-user uname`: file is owned by user "uname".

		> numeric user ID allowed.

	- `-ls`: list current file in `ls -dils` format on standard output.

	- `! expr`: True if "expr" is false.

		> This character will also usually need protection from interpretation by the shell.

		> `-not expr` same as `! expr`, but not POSIX compliant.

- `xargs [options] [command [initial-arguments]]`: build and execute command lines from standard input.

	Because Unix filenames can contain blanks and newlines, this default behavior is often problematic; filenames containing blanks and/or newlines are incorrectly processed by xargs. In these situations, it is better to use the `-0` option, which prevents such problems. When using this option, you will need to ensure that the program which produces the input for xargs also uses a null character as a separator.

	> If that program is GNU find for example, the `-print0` option does this for you.

Examples of usage:

- `find / -name passwd 2>/dev/null | xargs -ls`: build and execute command lines from standard input.

## 19 - Conexiones SSH

SSH (Secure Shell) is an access credential that is used in the SSH Protocol. In other words, it is a cryptographic network protocol that is used for transferring encrypted data over a network.

It always comes in a key pair:

1. Public key: everyone can see it; there is no need to protect it.

	> For encryption function.

2. Private key: stays on the computer; must be protected.

	> For decryption function.

### How does SSH work?

It uses asymmetric ciphers for encryption and decryption. The General procedure is:

1. Public keys from the local computers (system) are passed to the server, which is to be accessed.

2. The server then determines if the public key is registered.

3. If so, the server then creates a new secret key and encrypts it with the public key that was sent to it via a local computer.

4. This encrypted code is sent to the local computer.

5. This data is unlocked by the private key of the system and sent to the server.

6. The server, after receiving this data, verifies the local computer.

7. SSH creates a route, and all the encrypted data is transferred through it with no security issues.

SSH is key based authentication that is not prone to **brute-force attacks**.

### Bandit level 0

- `ssh bandit0@bandit.labs.overthewire.org -p 2220`: connect to the machine as the "bandit0".

	> The password for that user is `bandit0`.

### Bandit level 1

- `cat readme`: show the `readme` content.

	> The password for `bandit1` is `NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL`.

## 20 - Lectura de archivos especiales

### Bandit level 2

- `cat < -`: show the `-` content.

	> The password for `bandit2` is `rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi`.

## 21 - Lectura de archivos especiales

### Bandit level 3

- `cat "spaces in the filename"`: show the `spaces in the filename` content.

	> The password for `bandit3` is `aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG`.

## 22 - Directorios y archivos ocultos

### Bandit level 4

- `cat inhere/.hidden`: show the `.hidden` content.

	> The password for `bandit4` is `2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe`.

## 23 - Detección del tipo y formato de archivos

### Bandit level 5

- `find inhere/ -type f | xargs file`: see what file is human readable.

	> That file is `-file07`.

- `cat inhere/-file07`: show the `-file07` content.

	> The password for `bandit5` is `lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR`.

## 24 - Búsquedas precisas de archivos

### Bandit level 6

- `find inhere/ -type f -size 1033c -not -executable| xargs file`: find files that are $1033$ bytes in size and are not executable, to see which of those is human readable.

	> That file is `.file02`.

- `cat inhere/maybehere07/.file2`: show the `-file07` content.

	> The password for `bandit6` is `P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU`.

## 25 - Búsquedas precisas de archivos

### Bandit level 7

- `find / -type f -size 33c -user bandit7 -group bandit6 2> /dev/null | xargs file`: find files that have $33$ bytes, belonging to user "bandit7" and group "bandit6", to see which of them is human readable.

	> That file is `bandit7.password`.

- `cat /var/lib/dpkg/info/bandit7.password`: show the `bandit7.password` content.

	> The password for `bandit7` is `z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S`.

## 26 - Métodos de filtrado de datos

### Bandit level 8

- `cat data.txt | grep millionth`: display the content of the file data.txt and filter only the lines that contain the word "millionth".

	> The password for `bandit8` is `TESKZC0XvTetK0S9xNwm25STk5iWrBvP`.

## 27 - Métodos de filtrado de datos

- `sort`: write sorted concatenation of all FILE(s) to standard output.

	> With no FILE, or when FILE is `-`, read standard input.

	- `[OPTION]... [FILE]...`.

	- `[OPTION]... --files0-from=F`

- `uniq [OPTION]... [INPUT [OUTPUT]]`: filter adjacent matching lines from INPUT (or standard input), writing to OUTPUT (or standard output).

	> With no options, matching lines are merged into the first occurrence.

	- `-u` or `--unique`: only print unique lines.

## 28 - Métodos de filtrado de datos

### Bandit level 9

- `sort data.txt | uniq -u`: sort the lines in data.txt and then filter out only the unique line.

	> The password for `bandit9` is `EN632PlfYiZbn3PhVK3XOGSlNInNE00t`.

## 29 - Interpretación de archivos binarios

- `string`: print the sequences of printable characters in files.

	- `[-afovV] [-min-len]`.

	- `[-n min-len] [--bytes=min-len]`.

	- `[-t radix] [--radix=radix]`.

	- `[-e encoding] [--encoding=encoding]`.

	- `[-U method] [--unicode=method]`.

	- `[-] [--all] [--print-file-name]`.

	- `[-T bfdname] [--target=bfdname]`.

	- `[-w] [--include-all-whitespace]`.

	- `[-s] [--output-separator sep_string]`.

	- `[--help] [--version] file...`.

### Bandit level 10

- `strings data.txt | grep -E "=+"`: find human readable strings in data.txt that are preceded by several (more than one) `=`.

	> The password for `bandit10` is `G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s`.

## 30 - Codificación y decodificación en base64

- `base64 [OPTION]... [FILE]`: encode or decode FILE, or standard input, to standard output.

### Base 64

It is an encoding scheme that converts binary data into text format so that encoded textual data can be easily transported over a network uncorrupted and without any data loss.

---

- `base64 -d < data.txt`: decode the base64-encoded data in `data.txt` and display the password for "bandit11".

	> The password for `bandit11` is `6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM`.

## 31 - Cifrado césar y uso de `tr` para la traducción de caracteres

- `tr [-c|-C] [-s] string1 string2`: translate characters.

	- `string1 string2`: translation control strings. Each string shall represent a set of characters to be converted into an array of characters used for the translation.

The entire alphabet is `abcdefghijklmnopqrstuvwxyz` translates into `nopqrstuvwxyzabcdefghijklm`.

- `tr [A-Za-z] [N-ZA-Mn-za-m] data.txt`: translates (substitutes) each letter in the range A-Z and a-z according to the ROT13 cipher.

	> The password for `bandit12` is `nopqrstuvwxyzabcdefghijklm`.

## 32 - Creamos un descompresor recursivo automático de archivos en Bash