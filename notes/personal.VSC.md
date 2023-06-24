---
id: 71hhokeue0mejx9ixat6sor
title: VSC
desc: ''
updated: 1686604171624
created: 1679867204411
---

# Explorador de archivos

## Codificación

> Es el método que permite convertir un carácter de un lenguaje natural (como el de un alfabeto o silabario) en un símbolo de otro sistema de representación, como un número o una secuencia de pulsos electrónicos en un sistema electrónico aplicando normas o reglas de codificación.

Es como se muestran los caracteres en pantalla, dependiendo del valor (numérico) que este tenga asociado.

## Caracteres de acción o vacíos

Estos nos se le muestran al usuario, como por ejemplo un salto de linea:

- Windows utiliza dos caracteres.
- MacOS y Linux utilizan uno.

## Configuración de final de linea

- Windows utiliza `CR` (**Carriage Return**), MacOS y Linux `LF` (**Line Feed**).
- `CRLF` es una combinación de las dos anteriores.

> El problema de trabajar con equipos que usen diferente configuración en este apartado lo soluciona **git**.

# Atajos

## Usados

### `Ctrl`


- `↑ ↓` subir o bajar, recordando la posición del cursor.
- `← →` movernos entre palabras.
- `Shift + ← → o ↑ ↓` seleccionar palabras.
- `/` comentar lineas.
- `Shift + /` comentar bloques.
- `a` seleccionar todo.
- `e` cambiar el foco entre el explorador de archivos y el código.
- `<panel index>` cambiar el foco entre grupos.
- `Tab` cambiar entre los archivos abiertos en el grupo.
- `<number>` cambiar entre grupos.
- `r` ejecutar el archivo actual (Code Runner).
- `Shift + r` ejecutar el comando personalizado (Code Runner).
- `y` para rehacer.
- `l` buscar notas en Dendron.

### `Shift`

- `Tab` quitar tabulaciones.

### `Alt`

- `<tab index>` cambiar de pestaña.
- `↑ ↓` intercambiar la lineas.

- Paleta de comandos `F1`.

### Explorer

- `a` crear un nuevo archivo.

## Default

- `Tab` identar linea(s) seleccionadas.
- `Shift + Tab` identar linea(s) seleccionadas.
- `Ctrl + Alt + ↑ ↓` añadir cursor encima o abajo.
- `Shift + Alt + h` mostrar llamado de herencia.
- `Shift + Alt + ↑ ↓`
		- Copiar la linea superior o inferior.
		- Expandir selección.
- `Ctrl + k` Formatear lo seleccionado.
- `Ctrl + Shift + f` Buscar en archivos.
- `Ctrl + Enter` Insertar linea abajo.
- `Ctrl + Shift + Enter` Insertar linea arriba.

### Paleta de comandos

- Toggle activity bar visibility (bar v)

- Toggle primary sidebar bar visibility (side)

- Toggle zen mode (zen)

- Toggle Vertical/Horizontal layout (vert)

- Open file (file)

- Trim Trailing whitespace (trim)

- Unfold all