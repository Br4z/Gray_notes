---
id: t4lux2n7ddmt6vunm0mw4s2
title: 2-What is the shell?
desc: ''
updated: 1680489486815
created: 1680488911028
---

When we speak of the command line, we are really referring to the **shell**. The shell is a program that takes keyboard commands and passes them to the operating system to carry out. Almost all Linux distributions supply a shell program from the GNU Project called **bash**. The name is an acronym for **b**ourne-**a**gain **sh**ell, a reference to the fact that bash is an enhanced replacement for sh, the original Unix shell program written by Steve Bourne.

# Terminal emulators

When using a graphical user interface (GUI), we need another program called a **terminal** **emulator** to interact with the shell. If we look through our desktop menus, we will probably find one. KDE uses konsole, and GNOME uses gnome-terminal, though it's likely called simply Terminal on your menu. A number of other terminal emulators are available for Linux, but they all basically do the same thing: give us access to the shell. You will probably develop a preference for one or another terminal emulator based on the number of bells and whistles it has.

# Making your first keystrokes

```bash
[me@linuxbox ~]$
```

This is called a shell prompt, and it will appear whenever the shell is ready to accept input. While it might vary in appearance somewhat depending on the distribution, it will typically include your `username@machinename`, followed by the current working directory (more about that in a little bit) and a dollar sign. If the last character of the prompt is a hash mark (`#`) rather than a dollar sign, the terminal session has superuser privileges. This means either we are logged in as the root user or we selected a terminal emulator that provides superuser (administrative) privileges.

# Command history

Most Linux distributions remember the last 1,000 commands by default.

> **A few words about mice and focus**
>
> While the shell is all about the keyboard, you can also use a mouse with your terminal emulator. A mechanism built into the X Window System (the underlying engine that makes the GUI go) supports a quick copy-and-paste technique. If you highlight some text by holding down the left mouse button and dragging the mouse over it (or double-clicking a word), it is copied into a buffer maintained by X. Pressing the middle mouse button will cause the text to be pasted at the cursor location.
>
> Don't be tempted to use ctrl-C and ctrl-V to perform copy and paste inside a terminal window. They don't work. These control codes have different meanings to the shell and were assigned many years before the release of Microsoft Windows.
>
> Your graphical desktop environment (most likely KDE or GNOME), in an effort to behave like Windows, probably has its focus policy set to "click to focus." This means for a window to get focus (become active), you need to click on it. This is contrary to the traditional X behavior of "focus follows mouse," which means that a window gets focus just by passing the mouse over it. The window will not come to the foreground until you click on it, but it will be able to receive input. Setting the focus policy to "focus follows mouse" will make the copy-and-paste technique even more useful. Give it a try if you can (some desktop environments, such as Ubuntu's Unity no longer support it). I think if you give it a chance, you will prefer it.


# Try Some Simple Commands

```bash
date
cal  -> Display the Calendar
df   -> Display the current amount of free space on our disk drives
free -> Display the amount of free memory
exit -> Close the terminal emulator window or you can also use ctlr-D
```

> **The console behind the curtain**
>
> Even if we have no terminal emulator running, several terminal sessions continue to run behind the graphical desktop. We can access these sessions, called virtual consoles, by pressing `CTRL-ALT-F1` through `CTRL-ALT-F6` on most Linux distributions. When a session is accessed, it presents a login prompt into which we can enter our username and password. To switch from one virtual console to another, press `ALT-F1` through `ALT-F6`. On most systems, we can return to the graphical desktop by pressing `ALT-F7`.