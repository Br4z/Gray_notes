---
id: swlxxpk20nnnwgi3u3tap73
title: 11-Processes
desc: ''
updated: 1686276740880
created: 1686014355265
---

```BASH
ps       # Report a snapshot of current processes
top      # Display tasks
jobs     # List active jobs
bg       # Place a job in the background
fg       # Place a job in the foreground
kill     # Send a signal to a process
killall  # Kill processe by name
shutdwon # Shut down or reboot the system
```

## How a process works

When a system starts up, the kernel initiates a few of its own activities as processes and launches a program called `init. init`, in turn, runs a series of shell scripts (located in `/etc`) called init scripts, which start all the system services.

Like files, processes also have owners and user IDs, effective user IDs, and so on.

## Viewing processes

```BASH
ps # Show the processes associated with the current terminal session

ps x # Show the list of every process that we own
```

> With the `x` option, a new column called `STAT` was added.

| State |                                                                             Meaning                                                                              |
|:-----:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|  `R`  |                                                   Running. This means the process is running or ready to run.                                                    |
|  `S`  |                         Sleeping. The process is not running; rather, it is waiting for an event, such as a keystroke or network packet.                         |
|  `D`  |                                           Uninterruptible sleep. The process is waiting for I/O such as a disk drive.                                            |
|  `T`  |                                                        Stopped. The process has been instructed to stop.                                                         |
|  `Z`  |                      A defunct or "zombie" process. This is a child process that has terminated but has not been cleaned up by its parent.                       |
|  `<`  |   A high-priority process. It's possible to grant more importance to a process, giving it more time on the CPU. This property of a process is called niceness.   |
|  `N`  | A low-priority process. A process with low priority (a nice process) will get processor time only after other processes with higher priority have been serviced. |

> The process state may be followed by other characters.

```BASH
ps aux # Show the processes belonging to every user
```

Using the options without the leading dash invokes the command with "BSD-style" behavior.

| Header  |                                              Meaning                                              |
|:-------:|:-------------------------------------------------------------------------------------------------:|
| `USER`  |                            User ID. This is the owner of the process.                             |
| `%CPU`  |                                       CPU usage in percent.                                       |
| `%MEM`  |                                     Memory usage in percent.                                      |
|  `VSZ`  |                                       Virtual memory size.                                        |
|  `RSS`  | Resident set size. This is the amount of physical memory (RAM) the process is using in kilobytes. |
| `START` |             Time when the process started. For values over 24 hours, a date is used.              |

### Viewing processes dynamically with top

```BASH
top

# top - 14:59:20 up 6:30, 2 users, load average: 0.07, 0.02, 0.00
# Tasks: 109 total, 1 running, 106 sleeping, 0 stopped, 2 zombie
# Cpu(s): 0.7%us, 1.0%sy, 0.0%ni, 98.3%id, 0.0%wa, 0.0%hi, 0.0%si
# Mem: 319496k total, 314860k used, 4636k free, 19392k buff
# Swap: 875500k total, 149128k used, 726372k free, 114676k cach
```

The `top` program displays a continuously updating (by default, every three seconds) display of the system processes listed in order of process activity. The `top` display consists of two parts: a system summary at the top of the display, followed by a table of processes sorted by CPU activity.

| Row |      Field      |                                                                      Meaning                                                                      |
|:---:|:---------------:|:-------------------------------------------------------------------------------------------------------------------------------------------------:|
|  1  |      `top`      |                                                         This is the name of the program.                                                          |
|     |   `14:59:20`    |                                                         This is the current time of day.                                                          |
|     |    `up 6:30`    |                               This is called _uptime_. It is the amount of time since the machine was last booted.                                |
|     |    `2 users`    |                                                          There are two users logged in.                                                           |
|     | `load average:` | refers to the number of processes that are waiting to run; that is, the number of processes that are in a runnable state and are sharing the CPU. |
|  2  |    `Tasks:`     |                                     This summarizes the number of processes and their various process states.                                     |
|     |    `0.7%us`     |                                7% of the CPU is being used for **user** processes (processes outside the kernel).                                 |
|     |    `1.0%sys`    |                                          1% of the CPU is being used for **system** (kernel) processes.                                           |
|     |    `0.0%ni`     |                                          0% of the CPU is being used by "nice" (low-priority) processes.                                          |
|     |    `98.3%id`    |                                                             98.3% of the CPU is idle                                                              |
|     |    `0.0%id`     |                                                         0% of the CPU is waiting for I/O.                                                         |
|  4  |     `Mem:`      |                                                     This shows how physical RAM is being used                                                     |
|  5  |     `Swap:`     |                                            This shows how  swap space (virtual memory) is being used.                                             |

## Controlling processes

### Interrupting a process

In a terminal, pressing `CTRL + c` _interrupts_ a program. This means we are politely asking the program to terminate.

> Many (but not all) command line programs can be interrupted by using this technique.

### Putting a process in the background

Think of the terminal as having a **foreground** (with stuff visible on the surface, like the shell prompt) and a **background** (with stuff hidden behind the surface). To launch a program in the background, we can follow the command with an ampersand (`&`) character.

```BASH
xlogo &

# [1] 28236
```

The returned message is part of a shell feature called **job control**. With this message, the shell is telling us that we have started job number 1 (`[1]`) and that it has PID 28236.

```BASH
ps

#   PID TTY TIME CMD
# 10603 pts/1 00:00:00 bash
# 28236 pts/1 00:00:00 xlogo
# 28239 pts/1 00:00:00 ps
```

The shell's job control facility also gives us a way to list the jobs that have been launched from our terminal.

```BASH
jobs

# [1]+ Running    xlogo &
```

### Returning a process to the foreground

To return a process to the foreground, use the `fg` command.

```BASH
jobs

# [1]+ Running

# ---------------------------------- # ---------------------------------- #

fg %1

# xlogo
```

After that, the job with the job number (called **jobspec**) specified is returned to the foreground.

### Stopping (pausing) a process

To stop
a foreground process and place it in the background, press `CTRL + z`.

```BASH
xlogo

# [1]+ Stopped

# ---------------------------------- # ---------------------------------- #

bg %1

# [1]+ xlogo &
```

Why would we want to launch a graphical program from the command line? There are two reasons:

- The program you want to run might not be listed on the window manager's menus (such as xlogo).

- By launching a program from the command line, you might be able to see error messages that would otherwise be invisible if the program were launched graphically.

## Signals

The kill command is used to "kill" processes.

```BASH
xlogo &

# [1] 28401

# ---------------------------------- # ---------------------------------- #

kill 28401

# [1]+ Terminated    xlogo
```

The kill command doesn't exactly "kill" processes; rather, it sends them signals. Signals are one of several ways that the operating system communicates with programs.

- `CTRL + c`: sent a signal called INT (interrupt).
- `CTRL + z`: sent a signal called TSTP (terminal stop).

> Programs, in turn, "listen" for signals and may act upon them as they are received.

### Sending signals to processes with `kill`

```BASH
# kill -<signal> PID...
```

If no signal is specified on the command line, then the TERM (terminate) signal is sent by default.

| Number | Name  |                                                                                                                 Meaning                                                                                                                  |
|:------:|:-----:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|   1    |  HUP  |                                                                         The signal is used to indicate to programs that the controlling terminal has "hung up".                                                                          |
|   2    |  INT  |                                                                             Interrupt. This performs the same function as `CTRL + c` sent from the terminal.                                                                             |
|   3    | QUIT  |                                                                                                                                                                                                                                          |
|   9    | KILL  | Whereas programs may choose to handle signals sent to them in different ways, including ignoring them all together, the KILL signal is never actually sent to the target program. Rather, the kernel immediately terminates the process. |
|   11   | SEGV  |                                        Segmentation violation. This signal is sent if a program makes illegal use of memory; that is, if it tried to write somewhere it was not allowed to write.                                        |
|   15   | TERM  |                                                                          Terminate. If a program is still "alive" enough to receive signals, it will terminate.                                                                          |
|   18   | CONT  |                                                          Continue. This will restore a process after a STOP or TSTP signal. This signal is sent by the `bg` and `fg` commands.                                                           |
|   19   | STOP  |                                          This signal causes a process to pause without terminating. Like the KILL signal, it is not sent to the target process, and thus it cannot be ignored.                                           |
|   20   | TSTP  |                     Terminal stop. This is the signal sent by the terminal when `CTRL + z` is pressed. Unlike the STOP signal, the TSTP signal is received by the program, but the program may choose to ignore it.                      |
|   28   | WINCH |                                                                             Window change. This is the signal sent by the system when a window changes size.                                                                             |

> We could have also specified the process using a jobspec (for example, `%1`) instead of a PID.

Processes, like files, have owners, and you must be the owner of a process (or the superuser) to send it signals with `kill`.

### Sending signals to multiple processes with `killall`

It's also possible to send signals to multiple processes matching a specified program or username by using the `killall` command.

```BASH
# killall [-u user] [-signal] name...

xlogo &

# [1] 18801

xlogo &

# [2] 18802

killall xlogo

# [1]- Terminated xlogo
# [2]+ Terminated xlogo
```

## Shutting down the system

```BASH
halt
poweroff
reboot
shutdown
```

The process of shutting down the system involves the orderly termination of all the processes on the system, as well as performing some vital housekeeping chores (such as syncing all of the mounted file systems) before the system powers off.

The `shutdown` command is a bit more interesting. With it, we can specify which of the actions to perform (halt, power down, or reboot) and provide a time delay to the shutdown event.

```BASH
sudo shutdown -h now # Shutdown
sudo shutdown -r now # Reboot
```

## More process-related commands

| Command  |                                                   Description                                                    |
|:--------:|:----------------------------------------------------------------------------------------------------------------:|
| `pstree` | Outputs a process list arranged in a tree-like pattern showing the parent-child relationships between processes. |
| `vmstat`  |                                       Outputs a snapshot of system resource usage including memory, swap,
and disk I/O.                                        |
| `xload`  |                                     Memory usage in percent.                                      |
|  `tload`  |                                       Similar to the xload program but draws the graph in the terminal.                                        |
