## fesh

Un generador de feeds de Atom para cápsulas [Gemini](https://gemini.circumlunar.space/) escrito en POSIX `sh`.

## Dependencias

* `sh`, `bash`, `zsh` u otro shell de tipo UNIX.
* GNU Coreutils, BusyBox, Toybox, sbase u otro paquete de herramientas de UNIX.
* Opcional `date -r` (no es POSIX), de lo contrario utiliza la fecha actual.

## Referencias

* [Estructura de un feed de Atom por la W3C.](https://validator.w3.org/feed/docs/atom.html)


## Licencia

```text
fesh - Un generador de feeds de Atom para cápsulas Gemini escrito en POSIX sh.

Copyright (C) 2021 - Ricardo García Jiménez <ricardogj08@riseup.net>

Autorizado en virtud de la Licencia de Apache, Versión 2.0 (la "Licencia");
se prohíbe utilizar este software excepto en cumplimiento de la Licencia.
Podrá obtener una copia de la Licencia en:

	http://www.apache.org/licenses/LICENSE-2.0

A menos que lo exijan las leyes pertinentes o se haya establecido por escrito,
el software distribuido en virtud de la Licencia se distribuye “TAL CUAL”,
SIN GARANTÍAS NI CONDICIONES DE NINGÚN TIPO, ya sean expresas o implícitas.
Véase la Licencia para consultar el texto específico relativo a los permisos
y limitaciones establecidos en la Licencia.
```

## Registro de cambios

* versión 2.0
	* El parámetro `-r` es opcional (por defecto utiliza la ruta de trabajo actual).
	* El parámetro `-i` es reemplazado por `-d` con el dominio de la cápsula sin `gemini://`
