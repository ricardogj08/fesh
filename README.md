## fesh

Un generador de feeds de Atom para cápsulas [Gemini](https://gemini.circumlunar.space/) escrito en POSIX `sh`.

## Dependencias

* `sh`, `bash`, `zsh` u otro shell de tipo UNIX.
* GNU Coreutils, BusyBox, Toybox, sbase u otro paquete de herramientas de UNIX.
* Opcional `date -r` (no es POSIX), de lo contrario utiliza la fecha actual.

## Uso

### Consideraciones

Todos los archivos de un sitio web en Gemini (cápsula), deben contener al menos un título principal. `fesh` define el título de las entradas utilizando la primera aparición de un encabezado (título) de nivel 1 de un documento escrito en el lenguaje de marcado Gemini. Es recomendable seguir una estructura semejante a lo siguiente:

```markdown
# Título principal

Contenido...

## A

Contenido...

## B

### B-1

Contenido...

### B-2

Contenido...

## C

Contenido...

...
...
...
```

`fesh` escanea recursivamente el directorio raíz de una cápsula, y obtiene las entradas para el feed de Atom basado en la fecha de modificación más reciente (cuando es posible) de todos los archivos con extensión `*.gmi` y `*.gemini`. Ignora todos los archivos `index.gmi` e `index.gemini` para las entradas.

El feed de Atom generado se debe ubicar en la raíz de la carpeta de tu cápsula en el servidor Gemini.

### Primeros pasos

Genera un feed de Atom utilizando el directorio raíz de tu cápsula:

`$ fesh -d miblog.com -t 'Mi blog' -r ~/miblog`

Por defecto, `fesh` genera un archivo `atom.xml` en el directorio de trabajo actual. Copia el archivo `atom.xml` en la raíz de la carpeta de tu cápsula en el servidor Gemini:

`$ cp atom.xml /var/gemini/miblog/`

O en un solo paso:

`$ fesh -d miblog.com -t 'Mi blog' -r ~/miblog -o /var/gemini/miblog/atom.xml`

Ahora puedes difundir las nuevas publicaciones de tu cápsula compartiendo la URL Gemini `gemini://miblog.com/atom.xml`. Una buena idea es colocar un enlace del feed en tu cápsula o agregarlo en un servicio web Gemini agregador de feeds con soporte de Atom:

* CAPCOM Geminispace aggregator:
	* gemini://gemini.circumlunar.space/capcom/
* PlanetaLibre versión Gemini:
	* gemini://reisub.nsupdate.info/planetalibre/

Cuando modifiques o agregues nuevo contenido a tu cápsula, repite el mismo procedimiento para actualizar tu feed.

## Referencias

* [Especificación POSIX por el IEEE.](https://pubs.opengroup.org/onlinepubs/9699919799/utilities/contents.html)
* [Colección de alternativas POSIX `sh` a procesos externos por Dylan Araps.](https://github.com/dylanaraps/pure-sh-bible)
* [Tutoriales sobre UNIX por Bruce Barnett.](https://www.grymoire.com/Unix/index.html)
* [Estructura de un feed de Atom por la W3C.](https://validator.w3.org/feed/docs/atom.html)
* [Estructura de un feed RSS en `bash`.](https://github.com/cfenollosa/bashblog)
* [Gemfeed, un generador de feeds de Atom para Gemini escrito en `Python 3`.](https://tildegit.org/solderpunk/gemfeed)
* [GemAtom, un generador de feeds de Atom para Gemini escrito en `Rust`.](https://git.sr.ht/~dr_tutut/gematom)

## Licencia

```text
fesh - Un generador de feeds de Atom para cápsulas Gemini escrito en POSIX sh.

Copyright (C) 2021-2022 - Ricardo García Jiménez <ricardogj08@riseup.net>

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

> [Licencia de Apache Versión 2.0 en español.](https://wikis.fdi.ucm.es/ELP/Licencia_Apache)

## Registro de cambios

* Versión 2.0
	* El parámetro `-r` es opcional (por defecto utiliza la ruta de trabajo actual).
	* El parámetro `-i` fue reemplazado por `-d` para definir el dominio de la cápsula, ahora sin `gemini://`
	* Los parámetros `-c`, `-e` y `-s`, fueron removidos.
