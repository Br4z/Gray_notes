---
id: ewh6c0wtcztw1dqlbmoitlk
title: Neovim
desc: 'All my Neovim - Vim knowledge'
updated: 1689802987592
created: 1689624589171
---

## Sources

- [Vimtutor](http://www2.geog.ucl.ac.uk/~plewis/teaching/unix/vimtutor).

	> Just run the Ex command `Tutor` (`:Tutor`).

- [Boost Your Coding Fu With VSCode and Vim](https://www.barbarianmeetscoding.com/boost-your-coding-fu-with-vscode-and-vim/table-of-contents) (book).

	> Author: Jaime Gonzalez Garcia.

- [Taller de Neovim 2021](https://www.youtube.com/watch?v=LFIp7-TGmNU) (video).

## Vimtutor

### Lesson 4.2: THE SEARCH COMMAND

- `<C-o>`: go back to where you came from (further).

- `<C-i>`: go back to where you came from (forward).

### Lesson 4.4: THE SUBSTITUTE COMMAND

- `:s/thee/the`: change the first "thee" in the current line for "the".

- `:s/thee/the/g`: change all "thee" in the current line for "the".

- `:1,3s/old/new/g`: change all "old" for "new" between 1 and 3 line (inclusive).

- `:%s/old/new/g`: change all "old" for "new" in the whole file.

- `:%s/old/new/gc`: change all "old" for "new" in the whole file, with a prompt asking for your confirmation (in each replacement).

### Lesson 5.1: HOW TO EXECUTE AN EXTERNAL COMMAND

- `:ls -a`: execute the `ls` command with the option (flag) `-a`.

### Lesson 5.2: MORE ON WRITING FILES

- `:w test`: save the current buffer in a file named test.

	> If we have anything selected (with visual mode), only the selected text will be saved.
	>
	> We will see a `:\'<, '>`.

### Lesson 5.4: RETRIEVING AND MERGING FILES

- `:r test`: paste the content of the test file above the cursor.

- `:r !ls`: paste the output of the `ls` command above the cursor.

### Lesson 6.3: ANOTHER WAY TO REPLACE

- `R`: replace more than one character.

### Lesson 7.1: GETTING HELP

- `:help c_CTRL-D`: get information about the `CTRL-D` shortcut in the command mode.

### Lesson 7.3: COMPLETION

- `CTRL + d`: list the possible commands for the current input in command mode.

- `TAB`: prompt a command list to complete the current command if the current input is insufficient to determinate which command you want to type.

## Boost Your Coding Fu With VSCode and Vim

### 6: Moving blazingly fast with the core Vim motions

#### Move horizontally word by word

- `ge`: jump to the end of a word backwards.

#### words and WORDs

A word in Vim is either:

- A sequence of letters, digits and numbers

- A sequence of other non-blank characters

> Not together.

But Vim also has the concept of special kinds of words (with letters, digits and numbers) that also include special characters like `.`, `(`, `{`, etc. They are called **WORDs**. To use the normal motions that act on a **word**, use capitalize letters instead.

- `gE`: jump to the end of a WORD backwards.

#### Move horizontally extremely

- `g_`: moves to the non-blank character at the end of a line.

#### Moving vertically

- `}`: jumps entire paragraphs downwards.

- `{`: jumps entire paragraphs upwards.

#### High precision vertical motions with search pattern

Use `*` to do a search for the word under the cursor (`#` to do the same backwards).

### 7: Editing like magic with Vim operators

You can use operators and motions together by following any of these patterns:

```BASH
## {operator}{count}{motion}
## {count}{operator}{motion}
```

- Operator: determines which action you want to perform.

- Count: allows you to multiply the effect of an operator by performing an action a count number of times.

- Motion: represents the piece of text to which to apply the action defined by the operator.

#### Useful operators

- `c` (change): change deletes a piece of text and then sends you into Insert mode so that you can continue typing.

	> Is like the `d` and `i` commands combined into one.

- `g~` (switch case): changes letters from lowercase to uppercase and back.

	> Use `gu` to make something lowercase and `gU` to make something uppercase.

- `>` (shift right): adds indentation.

- `<` (shift left): removes indentation.

#### Taking editing up a notch with text objects

What is a document composed of? Words, sentences, quoted text, paragraphs, blocks, (HTML) tags, etc. **These are text objects**.

```BASH
## {operator}{a | i}{text-object}
```

- `i`: inner.

- `a`: around.

The built-in text-objects are:

- `w`: word.

- `s`: sentence.

- `p`: paragraph.

- `b` (or `(` and `)`): block surrounded by `()`.

- `B` (or `{` and `}`): block surrounded by `{}`.

- `"`, `'` and `\``: quoted text.

- `<` and `>` block surrounded by `<>`.

- `t`: tag.

#### More shorthand text editing commands

- `x` is equivalent to `dl` and deletes the character under the cursor.

- `X` is equivalent to `dh` and deletes the character before the cursor.

- `s` is equivalent to `ch`, deletes the character under the cursor and puts you into Insert mode.

- `~` to switch case for a single character.

### 9: Inserting text a la vim

- `gi`: puts you into Insert mode at the last place you made a change.

- `CTRL + h`: delete the last character you typed.

- `CTRL + w`: delete the last word you typed.

- `CTRL + u`: delete the last line you typed.

### 10: Selecting text in visual mode

- `v`: for visual mode character-wise. This mode lets you select text character by character.

- `V`: for visual mode line-wise. This other one lets you select text line by line.

- `CTRL + v`: for visual mode block-wise. This last mode lets you select text using rectangular blocks.

### 11: Switfly operating on search matches

- `gn`.

	- If you are on top of a search match, it selects the match in Visual mode.

	- If you are in Visual mode, it extends your current selection until the end of the next match.

	- If you are in Operator-pending mode, it operates on the next match.

- `gN`: does the same thing as `gn` but in inverse order.

### 12: Pushing the boundaries of copying and pasting

#### Pasting

- `gp`: same as `p` but puts the cursor after the pasted selection.

- `gP`: same as `P` and puts the cursor after the pasted selection.

#### Multi-copying and cutting with registers

- The unnamed register `"` is where you copy and cut stuff to, when you don't explicitly specify a register. The default register if you will.

- The named registers `a-z` are registers you can use explicitly to copy and cut text at will

- The yank register `0` stores the last thing you have yanked (copied).

- The cut registers `1-9` store the last 9 things you cut by using either the delete or the change command.

You can use the `:reg` command to see what is in your registers. Or you can type `:reg <register>` to inspect the contents of a specific register.

#### Pasting in insert mode

In insert mode using `CTRL + R + <register>` you can paste the contents of a register after the cursor.

### 13: Control vscode with command-line mode

#### Saving and closing files

- Use `:wall` (shorthand `:wa`) to save all files

- Use `:qall` (shorthand `:qa`) to close all files

- Use `:wqall` (shorthand `:wqa`) to save and close all files

- Use `:qall!` (shorthand `:qa!`) to close all files without saving

### 15: Surrounding things with vim surround

#### Deleting multiple lines at once

## Taller de Neovim 2021

### Shortcuts

- `^` ir al primer carácter no vació de una línea.

- `CTRL + y` desplazar el documento hacia arriba (sin mover el cursor).

- `CTRL + e` desplazar el documento hacia abajo (sin mover el cursor).

- `CTRL + u` subir (desplazando media página) manteniendo el cursor en la mitad.

- `CTRL + d` bajar (desplazando media página) manteniendo el cursor en la mitad.

- `CTRL + b` subir (desplazando una página) dejando el cursor en la parte inferior.

- `CTRL + f` bajar (desplazando una página) dejando el cursor en la parte superior.

- `s` sustituir (borrando el carácter donde estamos y entrando en modo insertar).

- `S` sustituir una línea entera (dejando el cursor al comienzo de esta).

- `r` reemplazar un carácter.

- `R` entrar en al modo remplazo en una línea.

- `%` si lo presionamos en un carácter de apertura o cierre ("(", ")", "[", "]"...) nos moverá el cursor a su contraparte.

- `P` pegar antes de donde está el cursor.

- `D` "borrar" hasta el final de la línea (teniendo como comienzo donde está el cursor).

- `yy` copiar una línea.

- `C` cambiar la línea (borrando y dejándonos en modo insertar desde donde estaba el cursor)

- `di<opening or closing character>` borrar lo que "encierra" el carácter de apertura y cierre.

- `da<opening or closing character>` lo mismo que el anterior, pero este es inclusivo.

	> En general es `<motion><a or i><opening or closing character>`.

- `df<character>` borra desde el cursor hasta donde está el carácter.

- `dt<character>` lo mismo que el anterior, pero este es excluyente.

- `f<character>` movernos a la coincidencia más cercana del carácter a nuestro cursor (hacia la derecha).

	> Si queremos ver la próxima coincidencia podemos usar `;`, lo mismo aplica para `t<character>`.

- `d/<string>` borra hasta que encuentre la coincidencia (empezando desde nuestro cursor), inclusivamente.

- Podemos buscar cadenas con `/cadena` y podemos usar `n` y `N` para navegar entre las coincidencias.

	> `?<string>` invierte el sentido de la búsqueda.

- `d?<string>` borrar hasta una coincidencia anterior (empezando desde nuestro cursor), inclusivamente.

- `*` buscamos las ocurrencias de la palabra sobre la que está el cursor (con `*` saltamos a la siguiente ocurrencia y con `#` retrocedemos).

- `.` repite la última acción.

- `g<basic motion>` realiza el movimiento en las líneas que se ven en pantalla.

	> Útil para cuando activas `wrap`.

- `gui<opening or closing character>` poner todas las letras en minúscula dentro de lo que encierra el carácter de apertura y cierre.

	> Con `U` podemos ponerlo en mayúsculas.

### Sustituciones

- `s/,/#/g` sustituye todas las `,` por `#` en la línea actual.

- `%s/,/#/g`sustituye todas las `,` por `#` en todo el fichero.

- `%s\v(def) ([^\(]+)(\([^\)]+\))\3 \2 \1` para invertir las definiciones de las funciones.

- `g/^[^e]\+|[aiou]/d` borrar las palabras que no tengan a la "e" como su única vocal.