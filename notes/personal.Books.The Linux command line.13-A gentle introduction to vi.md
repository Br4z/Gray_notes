---
id: iq4kyg7zsdsbub86dru62c4
title: 13-A gentle introduction to vi
desc: ''
updated: 1686523748209
created: 1686418378016
---

## Basic editing

### Joining lines

vi is rather strict about its idea of a line. Normally, it is not possible to move the cursor to the end of a line and delete the end-of-line character to join one line with the one below it. Because of this, vi provides a specific command, `J`, to join lines together.

## Search-and-replace

### Global Search-and-Replace

vi uses an ex command to perform search-and-replace operations (called **substitution** in vi) over a range of lines or the entire file.

```
:%s/Line/line/g
```

|     Item      |                                                            Meaning                                                            |
|:-------------:|:-----------------------------------------------------------------------------------------------------------------------------:|
|      `:`      |                                         The colon character starts an **ex** command.                                         |
|      `%`      |      This specifies the range of lines for the operation. % is a shortcut, meaning from the first line to the last line.      |
|      `s`      |                                This specifies the operation. In this case, it's substitution.                                 |
| `/Line/line/` |                                  This specifies the search pattern and the replacement text.                                  |
|      `g`      | This means "global" in the sense that the search-and-replace is performed on every instance of the search string in the line. |

A `c` can be added after `g` if you want it to ask for confirmation after each substitution.

```
:%s/Line/line/gc

replace with Line (y/n/a/q/l/^E/^Y)?
```

|          Item          |                                    Meaning                                    |
|:----------------------:|:-----------------------------------------------------------------------------:|
|          `n`           |                      Skip this instance of the pattern.                       |
|          `a`           | Perform the substitution on this and all subsequent instances of the pattern. |
|      `q` or `ESC`      |                              Quit substituting.                               |
|          `l`           |      Perform this substitution and then quit. This is short for "last".       |
| `CTRL + e`, `CTRL + y` |                   Scroll down and scroll up, respectively.                    |

## Editing multiple files

```BASH
vi file1 file2 file3...
```

### Switching between files

```
:bn Switch from one file to the next
:bp Move back to the previous file
:buffers View a list of files being edited
:buffer <buffer number> Switch to a specified buffer (file)
```

### Opening additional files for editing

It's also possible to add files to our current editing session.

```
:e file
```

### Inserting an entire file into another

It’s also possible to insert an entire file into one we are editing.

```
:r file
```

> It inserts the specified file below the cursor position.
