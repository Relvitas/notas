## WSL

El **Subsistema de Windows para Linux (WSL)** es una herramienta de Microsoft que permite ejecutar entornos Linux directamente en Windows, sin necesidad de máquinas virtuales o un arranque dual del sistema operativo.

:round_pushpin: Powershell modo administrador

```powershell
wsl --install
```

> Al finalizar la instalacion, reiniciar el sitema y, se abrira una shell de configuracion del susbsitema en donde se descargara el SO, y despues debemos asignar un usuario y contraseña.

---

## COMANDOS

Un comando puede ser:

1. Un programa ejecutable.
   
   /user/bin (binario)

2. Un comando de utilidad de la shell.
   
   Ya bienen dentro de la shell (is a shell builtin)

3. Una función de shell.
   
   Son funciones de shell esternas

4. Un alias.
   
   is aliased to 'ls --color=auto'

:fire: type

El comando `type` se usa para **mostrar información sobre cómo se ejecuta un comando** en el sistema.

```bash
# Sintaxis:
type [opciones] [comando]

# Opciones:
-t    Indica si el comando es un alias, función, palabra clave o binario.
-a    Muestra todas las ubicaciones donde se encuentra el comando.
-p    Muestra solo la ruta del ejecutable (si existe).
-f    Omite alias y funciones, mostrando solo comandos reales.
--help    Muestra la ayuda del comando type.
```

:fire: alias

El comando `alias` se usa para **crear atajos de comandos** en la terminal.

```bash
# Sintaxis de alias temporal:
alias nombre_alias='comando'

# Opciones:
alias    Muestra la lista de alias creados en la sesión actual.
alias nombre='comando'    Crea un alias con un nombre específico.
unalias nombre    Elimina un alias específico.
unalias -a    Elimina todos los alias de la sesión
```

:fire: |

El **pipe operator (`|`)** se usa en la terminal para **redirigir la salida de un comando como entrada de otro**.

```bash
ls | less
```

:fire: whoami

El comando `whoami` se usa para mostrar el nombre de usuario con el que se ha iniciado sesión en el sistema.

```bash
whoami
```

:fire: hostname

El comando `hostname` se usa para mostrar o establecer el nombre del sistema (host) en una red.

```bash
# Sintaxis:
hostname [opciones]

# Opciones:
-i    Muestra la dirección IP del host.    hostname -i
-I    Muestra todas las direcciones IP asignadas.    hostname -I
-d    Muestra el dominio del host.    hostname -d
-f    Muestra el nombre de host completo (FQDN).    hostname -f
-s    Muestra solo el nombre corto del host.    hostname -s
-V    Muestra la versión del comando.    hostname -V
```

:fire: id

El comando `id` se usa para mostrar el **UID (User ID), GID (Group ID) y grupos secundarios** del usuario actual o de un usuario específico.

```bash
# Sintaxis:
id [opciones] [usuario]

# Opciones:
-u    Muestra solo el UID del usuario.    id -u
-g    Muestra solo el GID del usuario.    id -g
-G    Muestra todos los grupos a los que pertenece el usuario.    id -G
-n    Muestra el nombre en lugar del ID.    id -un
-r    Muestra el ID real en lugar del efectivo.    id -ur
```

:fire: su

El comando `su` (**substitute user**) permite cambiar de usuario en la terminal, generalmente para obtener privilegios de superusuario (root).

```bash
# Sintaxis:
su [opciones] [usuario]

# Opciones:
- o -l    Inicia sesión con el entorno del usuario objetivo.    su - usuario
-c "comando"    Ejecuta un comando como otro usuario.    su -c "ls /root" root
-s /bin/bash    Especifica un shell diferente.    su -s /bin/sh usuario
```

:fire: sudo

El comando `sudo` (**superuser do**) permite ejecutar comandos con privilegios de **superusuario (root)** o de otro usuario sin necesidad de cambiar completamente de sesión.

```bash
# Sintaxis:
sudo [opciones] [comando]

# Opciones:
-u usuario    Ejecuta el comando como otro usuario.    sudo -u usuario whoami
-k    Fuerza a solicitar la contraseña en el siguiente uso de sudo.    sudo -k
-i    Inicia sesión como root con su entorno.    sudo -i
-s    Abre una shell con privilegios de root.    sudo -s
-l    Muestra los comandos que el usuario puede ejecutar con sudo.    sudo -l
```

:fire: passwd

El comando `passwd` se usa para cambiar la contraseña de un usuario en el sistema.

```bash
# Sintaxis:
passwd [opciones] [usuario]

# Opciones:
-d    Elimina la contraseña del usuario.    sudo passwd -d usuario
-e    Fuerza al usuario a cambiar su contraseña en el próximo inicio de sesión.    sudo passwd -e usuario
-l    Bloquea la cuenta del usuario.    sudo passwd -l usuario
-u    Desbloquea la cuenta del usuario.    sudo passwd -u usuario
-S    Muestra el estado de la cuenta de un usuario.    passwd -S usuario
```

:fire: grep

El comando `grep` se usa para **buscar patrones de texto** dentro de archivos o la salida de otros comandos.

```bash
# Sintaxis:
grep [opciones] "patrón" [archivo]

# Opciones:
-i    Ignora mayúsculas y minúsculas.    grep -i "error" archivo.txt
-v    Muestra las líneas que no coinciden con el patrón.    grep -v "error" archivo.txt
-r    Busca en archivos dentro de subdirectorios.    grep -r "error" /var/log/
-l    Muestra solo los nombres de los archivos donde se encontró el patrón.    grep -l "error" *.log
-c    Muestra el número de coincidencias.    grep -c "error" archivo.txt
-n    Muestra el número de línea donde aparece el patrón.    grep -n "error" archivo.txt
-w    Busca palabras completas.    grep -w "error" archivo.txt
-A N    Muestra N líneas después de una coincidencia.    grep -A 3 "error" archivo.txt
-B N    Muestra N líneas antes de una coincidencia.    grep -B 3 "error" archivo.txt
-C N    Muestra N líneas antes y después de una coincidencia.    grep -C 3 "error" archivo.txt
```

:fire: wc

El comando `wc` (**word count**) se usa para **contar líneas, palabras, caracteres y bytes** en archivos de texto o en la salida de otros comandos.

```bash
# Sintaxis:
wc [opciones] [archivo]

# Opciones:
-l    Muestra solo el número de líneas.    wc -l archivo.txt
-w    Muestra solo el número de palabras.    wc -w archivo.txt
-m    Muestra solo el número de caracteres.    wc -m archivo.txt
-c    Muestra solo el número de bytes.    wc -c archivo.txt
```

:fire: witch

El comando `which` se usa para encontrar la ubicación de un ejecutable dentro de los directorios especificados en la variable `PATH`.

```bash
# Sintaxis:
which [opciones] [comando]

# Opciones:
-a    Muestra todas las ubicaciones encontradas en PATH.    which -a python
```

:fire: find

El comando `find` se usa para buscar archivos y directorios en un sistema de archivos según diferentes criterios como **nombre, tipo, tamaño, permisos, fecha de modificación** y más.

```bash
# Sintaxis:
find [ruta] [opciones] [expresión]

# Opciones:
-name "archivo"    Busca por nombre exacto (sensible a mayúsculas).    find / -name "archivo.txt"
-iname "archivo"    Busca por nombre (ignora mayúsculas y minúsculas).    find / -iname "archivo.txt"
-type f    Busca solo archivos.    find /home -type f
-type d    Busca solo directorios.    find /var -type d
-size +10M    Busca archivos mayores a 10MB.    find /home -size +10M
-perm 755    Busca archivos con permisos 755.    find /home -perm 755
-user usuario    Busca archivos pertenecientes a un usuario.    find /home -user usuario
-mtime -7    Archivos modificados en los últimos 7 días.    find /home -mtime -7
-delete    Elimina los archivos encontrados.    find /tmp -name "*.log" -delete
-exec comando {} \;    Ejecuta un comando en cada archivo encontrado.    find /home -name "*.txt" -exec rm {} \;
```

> - **`ruta`**: Directorio donde buscar (ejemplo: `/home`).
> - **`opciones`**: Criterios de búsqueda (nombre, tipo, tamaño, etc.).
> - **`expresión`**: Acción a realizar con los resultados.

:fire: ls

`ls` (List) es un comando de Linux que se usa para **listar el contenido de un directorio**

```bash
ls [opcion] [ruta]
```

:fire: cd

El comando `cd` (**Change Directory**) se usa para navegar entre directorios en la terminal de Linux.

```bash
cd [ruta]
```

:fire: pwd

El comando `pwd` (**Print Working Directory**) muestra la ruta absoluta del directorio en el que te encuentras actualmente.

```bash
pwd [opciones]
```

:fire: file

El comando `file` se usa para identificar el **tipo de archivo** basándose en su contenido, no solo en su extensión.

```bash
# Sintaxis:
file [opciones] [archivo]

# Opciones:
-b Muestra solo el tipo de archivo, sin el nombre.
-i Muestra el tipo MIME del archivo.
-L Sigue enlaces simbólicos y analiza el archivo real.
-E Muestra información extendida sobre el archivo.
```

:fire: tree

El comando `tree` muestra la estructura de directorios y archivos en forma de árbol.

```bash
# Sintaxis
tree [opciones] [ruta]

# Opciones:
-a    Muestra todos los archivos, incluidos los ocultos.
-d    Muestra solo directorios.
-L n    Limita la profundidad del árbol a n niveles.
-f    Muestra la ruta completa de cada archivo.
-i    No dibuja líneas de conexión en la estructura.
-h    Muestra tamaños en formato legible (K, M, G).
-s    Muestra el tamaño de cada archivo.
-t    Ordena por fecha de modificación (más recientes primero).
-r    Invierte el orden de la lista.
-P "patrón"    Muestra solo archivos que coincidan con un patrón (Ejemplo: -P "*.txt").
--help    Muestra la ayuda del comando tree.
```

:fire: mkdir

El comando `mkdir` (**Make Directory**) se usa para crear nuevos directorios.

```bash
# Sintaxis
mkdir [opciones] [nombre_directorio]

# Opciones:
-p    Crea directorios anidados sin errores si ya existen.
-m MODE    Establece permisos al crear el directorio (Ejemplo: -m 755).
-v    Muestra un mensaje por cada directorio creado.
--help    Muestra la ayuda del comando mkdir.
```

:fire: touch

El comando `touch` se usa para **crear archivos vacíos** o **actualizar la fecha y hora de modificación** de un archivo existente.

```bash
# Sintaxis:
touch [opciones] [archivo]

# Opciones:
-a    Modifica solo la fecha de acceso, sin cambiar la de modificación.
-c    No crea el archivo si no existe (solo actualiza la fecha si existe).
-m    Modifica solo la fecha de modificación, sin cambiar la de acceso.
-t [[CC]YY]MMDDhhmm[.ss]    Establece una fecha/hora específica (Ejemplo: touch -t 202402141200 archivo.txt).
-d "YYYY-MM-DD HH:MM:SS"    Permite definir la fecha en un formato más flexible.
--help    Muestra la ayuda del comando touch.
```

:fire: cp

El comando `cp` (**copy**) se usa para **copiar archivos y directorios** en Linux.

```bash
# Sintaxis:
cp [opciones] [origen] [destino]

# Opciones:
-r    Copia directorios y su contenido de forma recursiva.
-i    Pide confirmación antes de sobrescribir archivos existentes.
-u    Copia solo si el archivo de origen es más reciente que el de destino.
-p    Mantiene permisos, propietario y marcas de tiempo del archivo original.
-v    Muestra detalles de los archivos copiados.
-n    No sobrescribe archivos existentes en el destino.
--backup    Crea una copia de seguridad de los archivos antes de sobrescribirlos.
--help    Muestra la ayuda del comando cp.
```

:fire: mv

El comando `mv` (**move**) se usa para **mover o renombrar archivos y directorios** en Linux.

```bash
# Sintaxis:
mv [opciones] [origen] [destino]

# Opciones:
-i    Pide confirmación antes de sobrescribir archivos existentes.
-u    Mueve solo si el archivo de origen es más reciente que el de destino.
-n    No sobrescribe archivos existentes en el destino.
-v    Muestra detalles de los archivos movidos o renombrados.
--backup    Crea una copia de seguridad antes de sobrescribir archivos.
--help    Muestra la ayuda del comando mv.
```

:fire: rm

El comando `rm` (**remove**) se usa para **eliminar archivos y directorios** en Linux.

```bash
# Sintaxis:
rm [opciones] [archivo/directorio]

# Opciones:
-r    Elimina directorios y su contenido de forma recursiva.
-i    Pide confirmación antes de eliminar cada archivo.
-f    Fuerza la eliminación sin pedir confirmación.
-v    Muestra detalles de los archivos eliminados.
--preserve-root    Protege el directorio raíz / de ser eliminado accidentalmente.
--help    Muestra la ayuda del comando rm.
```

> ⚠ **¡Precaución!** El uso de `rm -rf` puede eliminar archivos y directorios sin posibilidad de recuperación.

:fire: head

El comando `head` se usa para **mostrar las primeras líneas de un archivo** en Linux.

```bash
# Sintaxis:
head [opciones] [archivo]

# Opciones:
-n N    Muestra las primeras N líneas del archivo (por defecto son 10).
-c N    Muestra los primeros N bytes del archivo.
-q    No muestra los encabezados de los archivos cuando se usan múltiples archivos.
-v    Siempre muestra los encabezados de los archivos.
```

:fire: tail

El comando `tail` se usa para **mostrar las últimas líneas de un archivo** en Linux.

```bash
# Sintaxis:
tail [opciones] [archivo]

# Opciones:
-n N    Muestra las últimas N líneas del archivo (por defecto son 10).
-c N    Muestra los últimos N bytes del archivo.
-f    Muestra las nuevas líneas en tiempo real a medida que se agregan al archivo.
-q    No muestra los encabezados de los archivos cuando se usan múltiples archivos.
-v    Siempre muestra los encabezados de los archivos.
```

:fire: less

El comando `less` se usa para **visualizar archivos de texto de manera paginada**, permitiendo desplazarse hacia adelante y atrás sin cargar todo el archivo en memoria.

```bash
# Sintaxis:
less [opciones] [archivo]

# Opciones:
-N    Muestra los números de línea.
-S    Desactiva el ajuste de línea (permite desplazarse horizontalmente).
-X    No borra la pantalla al salir.
-F    Sale automáticamente si el archivo cabe en una sola pantalla.
-R    Interpreta caracteres de color y formato en archivos con salida ANSI.
```

:fire: cat

El comando `cat` (**concatenate**) se usa para leer, concatenar y mostrar el contenido de archivos en la terminal.

```bash
# Sintaxis:
cat [opciones] [archivo...]

# Opciones:
-n    Numera todas las líneas del archivo.    cat -n archivo.txt
-b    Numera solo las líneas que no están vacías.    cat -b archivo.txt
-s    Suprime líneas vacías repetidas.    cat -s archivo.txt
-E    Muestra $ al final de cada línea.    cat -E archivo.txt
-T    Muestra tabulaciones como ^I.    cat -T archivo.txt
>    Redirige la salida a un archivo (sobrescribe).    cat archivo1.txt > nuevo.txt
>>    Redirige la salida a un archivo (añade).    cat archivo1.txt >> nuevo.txt
```

:fire: Abrir programas

:round_pushpin: open (mac)

```bash
open [archivo]
```

:round_pushpin: xdg-open (linux)

```bash
xdg-open [archivo]
```

:fire: nautilus

El comando `nautilus` se usa para **abrir el explorador de archivos** en sistemas basados en GNOME, como Ubuntu.

```bash
# Sintaxis:
nautilus [opciones] [ruta]

# Opciones:
.    Abre el explorador en el directorio actual.
--browser    Abre Nautilus en modo explorador (con barra de navegación).
--no-desktop    Evita que Nautilus administre el escritorio.
--new-window    Abre una nueva ventana de Nautilus.
--select [archivo]    Abre Nautilus resaltando un archivo específico.
```

:fire: help

El comando `help` se usa para **mostrar información sobre comandos internos de Bash**.

```bash
# Sintaxis:
help [comando]

# Opciones:
help comando    Muestra la ayuda detallada de un comando específico.
-d    Muestra una breve descripción de cada comando.
-m    Muestra la ayuda en formato de página de manual (man).
-s    Muestra solo el formato de uso del comando.
```

:fire: man

El comando `man` se usa para **consultar el manual de referencia de los comandos y programas** en Linux.

```bash
# Sintaxis:
man [sección] [comando]

# Opciones:
man comando    Muestra el manual del comando especificado.
man -k palabra    Busca en los manuales comandos relacionados con la palabra clave.
man -f comando    Muestra una breve descripción del comando (equivalente a whatis).
man -a comando    Muestra todas las páginas del manual disponibles para el comando.
man -P pager comando    Especifica un paginador personalizado para visualizar el manual.
```

:fire: info

El comando `info` se usa para **mostrar documentación detallada** sobre comandos y programas en Linux, como alternativa a `man`.

```bash
# Sintaxis:
info [comando]

# Opciones:
info comando    Muestra la documentación del comando especificado.
info --subnodes comando    Expande automáticamente los nodos de la documentación.
info --all    Muestra todas las secciones disponibles del manual.
```

:fire: whatis

El comando `whatis` se usa para **mostrar una breve descripción de un comando o programa**, basada en su página de manual.

```bash
# Sintaxis:
whatis [comando]

# Opciones:
whatis comando    Muestra una breve descripción del comando especificado.
whatis -w palabra    Busca comandos que contengan la palabra clave.
whatis -s número comando    Limita la búsqueda a una sección específica del manual.
whatis -r expresión    Permite buscar comandos con una expresión regular.
```

---

## WILDCARDS

Las **wildcards** (comodines) en Linux son **símbolos especiales** que permiten hacer coincidencias con múltiples archivos o patrones en comandos de la terminal, facilitando la manipulación de archivos y directorios.

| Wildcard  | Descripción                                                                            | Ejemplo                      | Resultado                                                          |
| --------- | -------------------------------------------------------------------------------------- | ---------------------------- | ------------------------------------------------------------------ |
| `*`       | Coincide con **cualquier número de caracteres** (incluyendo ninguno).                  | `ls *.txt`                   | Lista todos los archivos `.txt` en el directorio.                  |
| `?`       | Coincide con **un solo carácter**.                                                     | `ls file?.txt`               | Coincide con `file1.txt`, `fileA.txt`, pero no con `file12.txt`.   |
| `[abc]`   | Coincide con **uno de los caracteres** especificados.                                  | `ls foto[12].jpg`            | Coincide con `foto1.jpg` y `foto2.jpg`, pero no con `foto3.jpg`.   |
| `[a-z]`   | Coincide con **un rango de caracteres**.                                               | `ls documento[a-c].txt`      | Coincide con `documentoa.txt`, `documentob.txt`, `documentoc.txt`. |
| `{a,b,c}` | Coincide con **cualquiera de los valores especificados**.                              | `ls {archivo1,archivo2}.txt` | Coincide con `archivo1.txt` y `archivo2.txt`.                      |
| `!`       | **Niega** un conjunto de caracteres.                                                   | `ls foto[!1].jpg`            | Coincide con todos los archivos `fotoX.jpg` excepto `foto1.jpg`.   |
| `**`      | Coincide con **todos los archivos y subdirectorios recursivamente** (solo en Bash 4+). | `ls **/*.txt`                | Encuentra todos los archivos `.txt` en subdirectorios.             |

:pushpin: Wildcards Avanzados

Estos wildcards requieren de activación.

```bash
shopt -s extglob # activar
shopt -u extglob # desactivar
```

| Wildcard  | Descripción                                     | Ejemplo                       |
| --------- | ----------------------------------------------- | ----------------------------- |
| !(patrón) | Excluye archivos que coincidan con el patrón.   | ls !(archivo.txt)             |
| @(patrón) | Coincide exactamente con el patrón.             | ls @(archivo\|documento).txt  |
| ?(patrón) | Coincide con cero o una ocurrencia del patrón.  | ls archivo?.txt               |
| *(patrón) | Coincide con cero o más ocurrencias del patrón. | ls archivo*.txt               |
| +(patrón) | Coincide con una o más ocurrencias del patrón.  | `ls +(archivo\|documento).txt |

:round_pushpin: POXIS

Los **clases de caracteres POSIX** como `[[:upper:]]` y `[[:lower:]]` son utilizadas en **expresiones regulares** y en **wildcards** en la terminal de Linux para hacer coincidencias con tipos específicos de caracteres.

| Clase          | Descripción                                                | Ejemplo                          | Coincide con                           |
| -------------- | ---------------------------------------------------------- | -------------------------------- | -------------------------------------- |
| `[[:upper:]]`  | Coincide con **letras mayúsculas**.                        | `ls *[[:upper:]]*.txt`           | `Archivo.txt`, `DATA.TXT`              |
| `[[:lower:]]`  | Coincide con **letras minúsculas**.                        | `ls *[[:lower:]]*.txt`           | `archivo.txt`, `notas.txt`             |
| `[[:digit:]]`  | Coincide con **números del 0 al 9**.                       | `ls *[[:digit:]]*.txt`           | `file1.txt`, `data2023.txt`            |
| `[[:alpha:]]`  | Coincide con **cualquier letra (mayúscula o minúscula)**.  | `ls *[[:alpha:]]*.txt`           | `documento.txt`, `ABC.txt`             |
| `[[:alnum:]]`  | Coincide con **letras y números**.                         | `ls *[[:alnum:]]*.txt`           | `file123.txt`, `abc456.txt`            |
| `[[:space:]]`  | Coincide con **espacios, tabulaciones y saltos de línea**. | `grep '[[:space:]]' archivo.txt` | Detecta líneas con espacios en blanco. |
| `[[:punct:]]`  | Coincide con **signos de puntuación**.                     | `ls *[[:punct:]]*.txt`           | `file!.txt`, `data?.txt`               |
| `[[:xdigit:]]` | Coincide con **dígitos hexadecimales (0-9, A-F, a-f)**.    | `ls *[[:xdigit:]]*.txt`          | `colorFF.txt`, `hashA9.txt`            |
| `[[:graph:]]`  | Coincide con **caracteres imprimibles excepto espacios**.  | `grep '[[:graph:]]' archivo.txt` | Todas las letras, números y signos.    |
| `[[:print:]]`  | Coincide con **caracteres imprimibles (incluye espacio)**. | `grep '[[:print:]]' archivo.txt` | Cualquier carácter visible.            |
| `[[:blank:]]`  | Coincide con **espacios y tabulaciones**.                  | `grep '[[:blank:]]' archivo.txt` | Espacios en blanco y `\t`.             |
| `[[:cntrl:]]`  | Coincide con **caracteres de control** (Ej: `\n`, `\t`).   | `grep '[[:cntrl:]]' archivo.txt` | Saltos de línea, tabulaciones.         |

---

## REDIRECCIONES

Las **redirecciones** permiten controlar la entrada y salida de comandos en la terminal, enviando o capturando datos desde archivos o dispositivos.

Shell:

1. stdin (0) es la entra - teclado

2. stdout (1) cuando obtenemos respuesta del comando

3. stderr (2) es el error que ocuerre cuando algo sale mal

| Símbolo  | Descripción                                                      | Ejemplo                                       | Explicación                                                     |
| -------- | ---------------------------------------------------------------- | --------------------------------------------- | --------------------------------------------------------------- |
| `>`      | Redirección de **salida estándar** (sobrescribe el archivo).     | `echo "Hola" > salida.txt`                    | Escribe `"Hola"` en `salida.txt`, sobrescribiendo su contenido. |
| `>>`     | Redirección de **salida estándar** (añade al archivo).           | `echo "Mundo" >> salida.txt`                  | Agrega `"Mundo"` al final de `salida.txt`.                      |
| `<`      | Redirección de **entrada estándar** desde un archivo.            | `wc -l < archivo.txt`                         | Cuenta las líneas de `archivo.txt`.                             |
| `2>`     | Redirección de **errores estándar** (sobrescribe).               | `ls /carpeta_no_existente 2> error.txt`       | Guarda el error en `error.txt`.                                 |
| `2>>`    | Redirección de **errores estándar** (añade al archivo).          | `ls /otra_carpeta_no_existente 2>> error.txt` | Agrega el error al final de `error.txt`.                        |
| `&>`     | Redirección de **salida y errores estándar** (sobrescribe).      | `comando &> salida.txt`                       | Guarda la salida y los errores en `salida.txt`.                 |
| `&>>`    | Redirección de **salida y errores estándar** (añade al archivo). | `comando &>> salida.txt`                      | Agrega salida y errores a `salida.txt`.                         |
| `>\|`    | Fuerza la sobrescritura, incluso si está activada `noclobber`.   | `echo "Texto" >\| protegido.txt`              | Sobrescribe `protegido.txt` aunque `noclobber` esté activo.     |
| `tee`    | Guarda la salida y la muestra en pantalla.                       | `ls \| tee salida.txt`                        | Muestra la salida en la terminal y la guarda en `salida.txt`.   |
| `tee -a` | Agrega la salida a un archivo sin sobrescribir.                  | `ls \| tee -a salida.txt`                     | Muestra la salida y la agrega a `salida.txt`.                   |

---

## OPERADORES DE CONTROL

Los **operadores de control** en Bash permiten ejecutar comandos de manera condicional o secuencial, controlando el flujo de ejecución.

| Operador | Descripción                                                    | Ejemplo                                           | Explicación                                                              |
| -------- | -------------------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------------------------------ |
| `;`      | Ejecuta múltiples comandos secuencialmente.                    | `comando1; comando2`                              | Ejecuta `comando1` y luego `comando2`, sin importar si el primero falla. |
| `&&`     | Ejecuta el segundo comando **solo si el primero tiene éxito**. | `mkdir nuevo_dir && cd nuevo_dir`                 | Crea `nuevo_dir` y solo si tiene éxito, entra en él.                     |
| `\||`    | Ejecuta el segundo comando **solo si el primero falla**.       | `ping -c 1 google.com \|| echo "No hay conexión"` | Si el `ping` falla, muestra `"No hay conexión"`.                         |
| `&`      | Ejecuta un comando en segundo plano.                           | `firefox &`                                       | Abre Firefox sin bloquear la terminal.                                   |
| `() `    | Ejecuta comandos en un **subshell**.                           | `(cd /tmp && ls)`                                 | Cambia a `/tmp`, lista archivos y luego vuelve al directorio original.   |
| `{}`     | Agrupa comandos en el mismo shell.                             | `{ cd /tmp; ls; }`                                | Cambia a `/tmp` y lista archivos en el mismo entorno.                    |
| `!`      | Invierte el resultado de un comando (negación).                | `! false`                                         | Retorna éxito (`true`), porque `false` es negado.                        |

---

## 

## PERMISOS

:pushpin: **Tipos de permisos en un archivo** usuario-grupo-otros usuarios

- r “read” → lectura
- w “write” → escritura
- x “execute” → ejecutar

:fire: ***añadir permisos a un fichero***

```bash
chmod tipoPermiso+ nomArchivo.ext
```

**Tipos:**

- u+(rwx) → permisos usuario
- g+(rwx) → permisos grupo
- o+(rwx) → permisos otros usuarios

:fire: ***quitar permisos a un fichero***

```bash
chmod tipoPermiso- nomArchivo.ext
```

**Tipos:**

- u-(rwx) → permisos usuario
- g-(rwx) → permisos grupo
- x-(rwx) → permisos otros usuarios

:fire: Asignar varios permisos a la vez

Los permisos se agregan separados por comas.

```bash
chmod u+r,g+w
```

:pushpin: Tabla de permisos

| ***Binario*** | ***Tipo Permiso*** | ***Decimal*** |
| ------------- | ------------------ | ------------- |
| 000           | - - -              | 0             |
| 001           | - - x              | 1             |
| 010           | - w -              | 2             |
| 011           | - w x              | 3             |
| 100           | r - -              | 4             |
| 101           | r - x              | 5             |
| 110           | r w -              | 6             |
| 111           | r w x              | 7             |

---

## VARIABLES DE ENTORNO

Las **variables de entorno** en Linux (y otros sistemas operativos tipo Unix) son **pares clave-valor** que almacenan información utilizada por el sistema y las aplicaciones. Estas variables afectan el comportamiento de los procesos en ejecución y pueden ser utilizadas en la terminal, scripts o programas.

:fire: printenv

El comando `printenv` muestra las **variables de entorno** definidas en el sistema.

```bash
# Sintaxis:
printenv [variable]
```

> Si se usa sin argumentos, muestra **todas** las variables de entorno.

:round_pushpin: Agregar variable al path

Estas modificaciones se deben agregar en el archivo .bashrc

```bash
PATH=$PATH:/nueva/ruta
```

> DESCRIPCION: Path es igual al contenido actual de path : pero agregale esta nueva ruta

---

## UTILIDADES DE RED

:fire: ifconfig

El comando `ifconfig` (**interface configurator**) se usa para **ver y configurar interfaces de red** en sistemas Unix/Linux. Sin embargo, en versiones modernas de Linux ha sido reemplazado por `ip a`.

```bash
# Sintaxis:
ifconfig [interfaz] [opciones]

# Opciones:
eth0    Muestra la configuración de la interfaz eth0.    ifconfig eth0
wlan0    Muestra la configuración de la interfaz WiFi wlan0.    ifconfig wlan0
up    Activa una interfaz de red.    ifconfig eth0 up
down    Desactiva una interfaz de red.    ifconfig eth0 down
netmask    Asigna una máscara de red.    ifconfig eth0 netmask 255.255.255.0
broadcast    Configura la dirección de broadcast.    ifconfig eth0 broadcast 192.168.1.255
mtu    Define el tamaño máximo de unidad de transmisión.    ifconfig eth0 mtu 1500
```

:fire: ping

El comando `ping` se usa para **verificar la conectividad de red** entre el equipo y otro host, midiendo el tiempo de respuesta.

```bash
# Sintaxis:
ping [opciones] [host]

# Opciones:
-c N    Envía solo N paquetes y se detiene.    ping -c 4 google.com
-i N    Intervalo entre paquetes en N segundos.    ping -i 2 google.com
-w N    Finaliza después de N segundos.    ping -w 5 google.com
-s N    Tamaño del paquete en bytes.    ping -s 128 google.com
-q    Muestra solo un resumen de la prueba.    ping -c 4 -q google.com
```

:fire: curl

El comando `curl` (**Client URL**) se usa para **transferir datos desde o hacia un servidor** a través de protocolos como HTTP, HTTPS, FTP, SCP, SFTP, LDAP, entre otros.

```bash
# Sintaxis:
curl [opciones] [URL]

# Opciones:
-o archivo    Guarda la respuesta en un archivo.    curl -o página.html https://example.com
-O    Guarda con el mismo nombre del archivo remoto.    curl -O https://example.com/index.html
-L    Sigue redirecciones.    curl -L https://short.url
-I    Obtiene solo los encabezados HTTP.    curl -I https://example.com
-X MÉTODO    Especifica el método HTTP.    curl -X POST https://api.example.com
-d "datos"    Envía datos en una solicitud POST.    curl -d "user=admin&pass=123" -X POST https://api.example.com
-H "Encabezado"    Añade un encabezado HTTP.    curl -H "Authorization: Bearer TOKEN" https://api.example.com
-u usuario:contraseña    Autenticación HTTP básica.    curl -u admin:123 https://example.com
```

:fire: wget

El comando `wget` se usa para **descargar archivos** desde la web utilizando protocolos como **HTTP, HTTPS y FTP**. Es útil para descargas automatizadas y en segundo plano.

```bash
# Sintaxis:
wget [opciones] [URL]


# Opciones:
-O archivo    Guarda con un nombre específico.    wget -O miarchivo.zip https://example.com/archivo.zip
-c    Reanuda una descarga interrumpida.    wget -c https://example.com/archivo.zip
-b    Descarga en segundo plano.    wget -b https://example.com/archivo.zip
-q    Descarga en modo silencioso (sin salida en pantalla).    wget -q https://example.com/archivo.zip
--limit-rate=100k    Limita la velocidad de descarga a 100 KB/s.    wget --limit-rate=100k https://example.com/archivo.zip
--no-check-certificate    Omite la verificación SSL en HTTPS.    wget --no-check-certificate https://example.com/archivo.zip
-r    Descarga recursivamente una web.    wget -r https://example.com
--user=usuario --password=clave    Autenticación en sitios protegidos.    wget --user=admin --password=123 https://example.com
```

:fire: traceroute

El comando `traceroute` se usa para **rastrear la ruta** que siguen los paquetes desde tu máquina hasta un destino en la red. Muestra cada nodo intermedio y el tiempo de respuesta.

```bash
# Sintaxis:
traceroute [opciones] [host]

# Opciones
-m N    Establece un máximo de N saltos.    traceroute -m 15 google.com
-q N    Número de paquetes por salto (por defecto 3).    traceroute -q 1 google.com
-w N    Tiempo de espera en segundos por respuesta.    traceroute -w 2 google.com
-I    Usa paquetes ICMP en lugar de UDP.    traceroute -I google.com
-T    Usa paquetes TCP en lugar de UDP.    traceroute -T google.com
```

:fire: netscat

El comando `netcat` (`nc`) es una herramienta versátil para **establecer conexiones de red, enviar datos y depurar servicios**. Puede actuar como **cliente o servidor** y soporta protocolos **TCP y UDP**.

```bash
# Sintaxis:
nc [opciones] [host] [puerto]

# Opciones:
-l    Activa modo escucha (servidor).    nc -l 1234
-v    Muestra detalles de la conexión.    nc -v google.com 80
-u    Usa UDP en lugar de TCP.    nc -u 192.168.1.1 53
-w N    Finaliza si no hay respuesta en N segundos.    nc -w 5 google.com 80
-z    Escanea puertos sin enviar datos.    nc -zv 192.168.1.1 22-80
-n    No resuelve nombres de dominio.    nc -n 192.168.1.1 443
```

---

## COMPRIMIR ARCHIVOS

:fire: tar

El comando `tar` (**Tape Archive**) se usa para **crear, extraer y gestionar archivos comprimidos o empaquetados** en Linux.

```bash
# Sintaxis:
tar [opciones] [archivo.tar] [archivos/directorios]

# Opciones:
-c    Crea un archivo tar.    tar -cvf archivo.tar carpeta/
-x    Extrae un archivo tar.    tar -xvf archivo.tar
-t    Lista el contenido sin extraerlo.    tar -tvf archivo.tar
-v    Muestra detalles de la operación.    tar -cvf archivo.tar carpeta/
-f    Especifica el nombre del archivo tar.    tar -xf archivo.tar
-z    Comprime con gzip (.tar.gz).    tar -czvf archivo.tar.gz carpeta/
-j    Comprime con bzip2 (.tar.bz2).    tar -cjvf archivo.tar.bz2 carpeta/
-J    Comprime con xz (.tar.xz).    tar -cJvf archivo.tar.xz carpeta/
```

:fire: zip

El comando `zip` se usa para **comprimir archivos y directorios** en un formato `.zip`, que es compatible con Windows y otros sistemas.

```bash
# Sintaxis:
zip [opciones] archivo.zip archivos/directorios

# Opciones:
-r    Comprime una carpeta recursivamente.    zip -r backup.zip carpeta/
-9    Usa la máxima compresión.    zip -9 archivo.zip archivo.txt
-e    Cifra el archivo con contraseña.    zip -e secreto.zip documento.txt
-m    Mueve archivos al .zip y los borra del origen.    zip -m backup.zip archivo.txt
-q    Modo silencioso (sin mostrar salida).    zip -q backup.zip carpeta/
-u    Agrega archivos nuevos o actualizados a un .zip existente.    zip -u backup.zip nuevo.txt
```

:fire: unzip

El comando `unzip` se usa para **extraer archivos y carpetas** de un archivo comprimido en formato `.zip`.

```bash
# Sintaxis:
unzip [opciones] archivo.zip

# Opciones:
-d    Extrae el contenido en un directorio específico.    unzip archivo.zip -d /ruta/destino
-l    Lista los archivos dentro del .zip sin extraerlos.    unzip -l archivo.zip
-t    Verifica si el .zip está corrupto.    unzip -t archivo.zip
-o    Sobrescribe archivos sin preguntar.    unzip -o archivo.zip
-q    Modo silencioso (no muestra salida).    unzip -q archivo.zip
-x    Excluye archivos específicos al extraer.    unzip archivo.zip -x "imagen.jpg"
-n    No sobrescribe archivos existentes.    unzip -n archivo.zip
```



---



## MANEJO PROCESOS

:fire: ps

El comando `ps` (**Process Status**) muestra **información sobre los procesos en ejecución** en el sistema.

```bash
# Sintaxis:
ps [opciones]

# Opciones:
-e    Muestra todos los procesos del sistema.    ps -e
-f    Muestra información detallada.    ps -ef
-u usuario    Filtra los procesos de un usuario específico.    ps -u root
-l    Muestra información en formato largo.    ps -l
-x    Muestra procesos sin terminal asociada.    ps -x
-aux    Lista todos los procesos con más detalles.    ps aux
--sort=-%mem    Ordena procesos por consumo de memoria.    ps aux --sort=-%mem
```

:fire: kill

El comando `kill` **envía señales a procesos** para terminarlos o modificarlos

```bash
# Sintaxis:
kill [opciones] PID

# Opciones:
-9    Mata el proceso forzosamente.    kill -9 1234
-15    Intenta terminar el proceso de forma segura (por defecto).    kill -15 1234
-l    Muestra la lista de señales disponibles.    kill -l
-SIGTERM    Envía la señal SIGTERM (equivalente a -15).    kill -SIGTERM 1234
-SIGKILL    Envía la señal SIGKILL (equivalente a -9).    kill -SIGKILL 1234
```

:fire: top

El comando `top` muestra en **tiempo real** información sobre el uso del sistema, incluyendo **procesos activos, consumo de CPU y memoria**.

```bash
# Sintaxis:
top [opciones]

# Opciones:
-d SEGUNDOS    Define el intervalo de actualización.    top -d 2 (actualiza cada 2s)
-u usuario    Filtra por usuario específico.    top -u root
-p PID    Muestra solo un proceso específico.    top -p 1234
-n N    Muestra N actualizaciones y sale.    top -n 5
-b    Modo batch (para scripts).    top -b -n 1 > salida.txt
```

:fire: htop

El comando `htop` es una alternativa mejorada a `top` para **monitorear procesos en tiempo real**, con una interfaz interactiva y más amigable.

```bash
# Sintaxis:
htop [opciones]

# Opciones:
-d N    Establece el retardo de actualización en décimas de segundo.    htop -d 10 (actualiza cada 1s)
-u usuario    Muestra solo los procesos de un usuario.    htop -u root
-s columna    Ordena por una columna específica.    htop -s %MEM (por uso de memoria)
-p PID    Muestra solo un proceso específico.    htop -p 1234
-C    Deshabilita colores en la interfaz.    htop -C
```

:fire: jobs

El comando `jobs` muestra una **lista de trabajos en segundo plano y en ejecución** en la terminal.

```bash
# Sintaxis:
jobs [opciones]

# Opciones:
-l    Muestra el PID de cada trabajo.    jobs -l
-p    Muestra solo los PID de los trabajos.    jobs -p
-r    Muestra solo los trabajos en ejecución.    jobs -r
-s    Muestra solo los trabajos detenidos.    jobs -s
```

:fire: fg

El comando `fg` **trae un proceso en segundo plano (background) de vuelta al primer plano (foreground)**.

```bash
# Sintaxis:
fg [%n]

# Ejemplo:
fg %1 # Trae al primer plano el trabajo número 1.
```

:fire: bg

El comando `bg` **reanuda un proceso pausado y lo envía a segundo plano (background)**.

```bash
# Sintaxis:
bg [%n]
```



---



## EDITORES DE TEXTO

:fire: vim

`vim` (**Vi IMproved**) es un editor de texto mejorado basado en `vi`, con soporte para **resaltado de sintaxis, múltiples deshacer, autocompletado y plugins.**

```bash
# Sintaxis:
vim [opciones] [archivo]

# Opciones:
i	Entra en modo inserción (antes del cursor).
a	Entra en modo inserción (después del cursor).
Esc	Vuelve al modo normal.
:w	Guarda el archivo.
:q	Cierra vim.
:wq o ZZ	Guarda y cierra.
:q!	Cierra sin guardar.
u	Deshacer el último cambio.
Ctrl + r	Rehacer el cambio deshecho.
```

> Navegacion en vim:
> 
> h    Mueve el cursor a la izquierda.
> l    Mueve el cursor a la derecha.
> j    Mueve el cursor hacia abajo.
> k    Mueve el cursor hacia arriba.
> gg    Va al inicio del archivo.
> G    Va al final del archivo.
> Ctrl + d    Baja media pantalla.
> Ctrl + u    Sube media pantalla.
> 
> 
> 
> Busqueda:
> 
> /palabra    Busca "palabra" en el texto.
> n    Busca la siguiente coincidencia.
> N    Busca la coincidencia anterior.
> 
> 
> 
> Cortar, copiar y pegar
> 
> yy    Copia la línea actual.
> dd    Corta la línea actual.
> p    Pega después del cursor.
> P    Pega antes del cursor.



---



## ARCHIVOS

:fire: .bash_history

Este es un archivo que almacena el historial de los comandos ingresados a la terminal.

```bash
~/.bash_history #ruta del archivo
```

:fire: .bashrc

El archivo **`.bashrc`** es un **script de configuración** que se ejecuta automáticamente cada vez que se inicia una nueva sesión de Bash en una terminal **no de login**.

```bash
~/.bashrc
```

> En este archivo se pueden agregar variables de entorno, alias ...
