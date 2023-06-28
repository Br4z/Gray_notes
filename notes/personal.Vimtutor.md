---
id: zs1o4vbpfx4qfhbw2ewqzdw
title: Vimtuto
desc: ''
updated: 1687831295730
created: 1687829986819
---

## Lesson 4.2: THE SEARCH COMMAND

- `<C-o>`: go back to where you came from (further).

- `<C-i>`: go back to where you came from (forward).

## Lesson 4.4: THE SUBSTITUTE COMMAND

- `:s/thee/the`: change the first "thee" in the current line for "the".

- `:s/thee/the/g`: change all "thee" in the current line for "the".

- `:1,3s/old/new/g`: change all "old" for "new" between 1 and 3 line (inclusive).

- `:%s/old/new/g`: change all "old" for "new" in the whole file.

- `:%s/old/new/gc`: change all "old" for "new" in the whole file with a prompt asking for your confirmation (in each replacement).