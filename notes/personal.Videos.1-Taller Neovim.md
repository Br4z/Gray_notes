---
id: w4z2tq83aceql0ztd94f0nn
title: 1-Taller Neovim
desc: ''
updated: 1686418553541
created: 1682892684931
video_title: Taller de Neovim 2021
date: 2023-02-28T00:00:00.000Z
source: https://www.youtube.com/watch?v=LFIp7-TGmNU
---

## Shortcuts

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

## Sustituciones

- `s/,/#/g` sustituye todas las `,` por `#` en la línea actual.
- `%s/,/#/g`sustituye todas las `,` por `#` en todo el fichero.
- `%s\v(def) ([^\(]+)(\([^\)]+\))\3 \2 \1` para invertir las definiciones de las funciones.
- `g/^[^e]\+|[aiou]/d` borrar las palabras que no tengan a la "e" como su única vocal.