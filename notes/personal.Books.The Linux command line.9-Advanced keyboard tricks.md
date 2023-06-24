---
id: j6pl0ef2s2mkdr7yte20a4h
title: 9-Advanced keyboard tricks
desc: ''
updated: 1685814809536
created: 1685210448603
---

## Command line editing

bash uses a library called **Readline** to implement command line editing.

### Cursor movement

|    Key     |                                               Action                                                |
|:----------:|:---------------------------------------------------------------------------------------------------:|
| `CTRL + a` |                            Move the cursor to the beginning of the line.                            |
| `CTRL + e` |                               Move the cursor to the end of the line.                               |
| `CTRL + f` |                   Move cursor forward one character; same as the right arrow key.                   |
| `CTRL + b` |                   Move cursor backward one character; same as the left arrow key.                   |
| `ALT + f`  |                                    Move cursor forward one word.                                    |
| `ALT + b`  |                                   Move cursor backward one word.                                    |
| `CTRL + l` | Clear the screen and move the cursor to the top-left corner. The clear command does the same thing. |

### Modifying Text

|        Key        |                                                                    Action                                                                     |
|:-----------------:|:---------------------------------------------------------------------------------------------------------------------------------------------:|
|    `CTRL + k`     |                                            Kill text from the cursor location to the end of the line.                                             |
|    `CTRL + u`     |                                       Kill text from the cursor location to the beginning of the line.                                        |
|     `ALT + d`     |                                      Kill text from the cursor location to the end of the current word.                                       |
| `ALT + BACKSPACE` | Kill text from the cursor location to the beginning of the current word. If the cursor is at the beginning of a word, kill the previous word. |
|    `CTRL + y`     |                                      Yank text from the kill-ring and insert it at the cursor location.                                       |

### Cutting and pasting (killing and yanking) text

Items that are cut are stored in a buffer (a temporary storage area in memory) called the **kill-ring**.

|    Key     |                                        Action                                        |
|:----------:|:------------------------------------------------------------------------------------:|
| `CTRL + d` |                     Delete the character at the cursor location.                     |
| `CTRL + t` | Transpose (exchange) the character at the cursor location with the one preceding it. |
| `ALT + t`  |         Transpose the word at the cursor location with the one preceding it.         |
| `ALT + l`  | Convert the characters from the cursor location to the end of the word to lowercase. |
| `ALT + u`  | Convert the characters from the cursor location to the end of the word to uppercase. |

## Completion

Completion occurs when you press the `TAb` key while typing a command.

|    Key    |                                                                    Action                                                                    |
|:---------:|:--------------------------------------------------------------------------------------------------------------------------------------------:|
| `ALT + ?` | Display a list of possible completions. On most systems, you can also do this by pressing the `TAB` key a second time, which is much easier. |
| `ALT + *` |                      Insert all possible completions. This is useful when you want to use more than one possible match.                      |
| `ALT + t` |                                     Transpose the word at the cursor location with the one preceding it.                                     |
| `ALT + l` |                             Convert the characters from the cursor location to the end of the word to lowercase.                             |
| `ALT + u` |                             Convert the characters from the cursor location to the end of the word to uppercase.                             |

## Using history

### Searching History

```BASH
history | less

# ---------------------------------- # ---------------------------------- #

history | greq /usr/bin # Display all commands we executed that contains the path "/usr/bin"

# ---------------------------------- # ---------------------------------- #

!259 # Get the command in the 259th line of the history
```

**Bash** also provides the ability to search the history list incrementally. This means we can tell bash to search the history list as we enter characters, with each additional character further refining our search. To start incremental search, press `CTRL + r` followed by the text you are looking for. When you find it, you can either press enter to execute the command or press `CTRL + j` to copy the line from the history list to the current command line. To find the next occurrence of the text (moving “up” the history list), press `CTRL + r` again.

|    Key     |                                                           Action                                                           |
|:----------:|:--------------------------------------------------------------------------------------------------------------------------:|
| `CTRL + P` |                        Move to the previous history entry. This is the same action as the up arrow.                        |
| `CTRL + N` |                         Move to the next history entry. This is the same action as the down arrow.                         |
| `ALT + <`  |                                      Move to the beginning (top) of the history list                                       |
| `ALT + >`  |                       Move to the end (bottom) of the history list, i.e., the current command line.                        |
| `ALT + p`  | Reverse search, nonincremental. With this key, type in the search string and press `ENTER` before the search is performed. |
| `ALT + n`  |                                              Forward search, nonincremental.                                               |
| `CTRL + o` |                         Execute the current item in the history list and advance to the next one.                          |

### History expansion

|     Key      |                        Action                         |
|:------------:|:-----------------------------------------------------:|
|     `!!`     |               Repeat the last command.                |
| `!<number>`  |          Repeat history list item _number_.           |
| `!<string>`  | Repeat last history list item starting with _string_. |
| `!?<string>` |  Repeat last history list item containing _string_.   |

> **Script**
>
> In addition to the command history feature in bash, most Linux distributions include a program called script that can be used to record an entire shell session and store it in a file.
>
> ```BASH
> script <file name>
> ```
>
> Where _file_ is the name of the file used for storing the recording. If no file is specified, the file typescript is used.
