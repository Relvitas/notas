**TREE(1)** Manual de comandos generales **TREE(1)**

## NOMBRE

   `tree - lista el contenido de directorios en un formato similar a un árbol.`

## SINOPSIS

   `tree  [-acdfghilnpqrstuvxACDFJQNSUX]  [-L nivel [-R]] [-H baseHREF] [-T    título] [-o archivo] [-P patrón] [-I patrón] [--gitignore] [--git‐    file[=]archivo] [--matchdirs] [--metafirst] [--ignore-case] [--nolinks]    [--hintro[=]archivo] [--houtro[=]archivo] [--inodes] [--device]    [--sort[=]nombre] [--dirsfirst] [--filesfirst] [--filelimit #] [--si]    [--du] [--prune] [--charset[=]X] [--timefmt[=]formato] [--fromfile]    [--fromtabfile] [--fflinks] [--info] [--infofile[=]archivo] [--noreport]    [--version] [--help] [--] [directorio ...]`

## DESCRIPCIÓN

   ``Tree es un programa de listado recursivo de directorios que produce una    lista con sangría según la profundidad de los archivos, la cual se    colorea al estilo de dircolors si la variable de entorno LS_COLORS está    configurada y la salida va a un tty. Sin argumentos, tree lista los    archivos en el directorio actual. Cuando se proporcionan argumentos de    directorio, tree lista todos los archivos y/o directorios encontrados en    los directorios dados, uno por uno. Al finalizar el listado de todos los    archivos/directorios encontrados, tree devuelve el número total de    archivos y/o directorios listados.    De forma predeterminada, cuando se encuentra un enlace simbólico, la    ruta a la que hace referencia se imprime después del nombre del enlace    en el formato:        nombre -> ruta-real    Si se proporciona la opción `-l` y el enlace simbólico apunta a un    directorio real, entonces tree seguirá la ruta del enlace simbólico como    si fuera un directorio real.``

## OPCIONES

   `Tree entiende los siguientes modificadores de línea de comandos:`

### OPCIONES DE LISTADO

   ``-a     Se imprimen todos los archivos. De forma predeterminada, tree no           imprime archivos ocultos (aquellos que comienzan con un punto          `.`). En ningún caso tree imprime las construcciones del sistema           de archivos `.` (directorio actual) y `..` (directorio padre).    -d     Lista solo directorios.    -l     Sigue enlaces simbólicos si apuntan a directorios, como si fueran           directorios reales. Se evitan los enlaces simbólicos que puedan           causar recursión cuando se detectan.    -f     Imprime la ruta completa para cada archivo.    -x     Permanece solo en el sistema de archivos actual. Similar a          `find -xdev`.    -L nivel           Profundidad máxima de visualización del árbol de directorios.    -R     Recorre recursivamente el árbol por niveles de directorio (ver la           opción -L) y en cada nivel genera un archivo llamado           00Tree.html (similar a -o).    -P patrón           Lista solo los archivos que coincidan con el patrón comodín.           Puede usar múltiples opciones -P. Nota: debe usar la opción -a           para que también se consideren los archivos que comienzan con un           punto `.`. Los operadores comodín válidos son `*` (cero o más           caracteres), `**` (cero o más caracteres incluyendo `/`), `?`           (un solo carácter), `[...]` (cualquier carácter listado entre           corchetes, con rangos opcionales como [A-Z]), `[^...]` (cualquier           carácter no listado), y `|` para separar patrones alternativos.           Un `/` al final del patrón coincide con directorios, pero no con           archivos.    -I patrón           No lista los archivos que coincidan con el patrón comodín. Puede           usar múltiples opciones -I. Consulte -P para más información.    --gitignore           Usa los archivos .gitignore de git para filtrar archivos y           directorios. También usa $GIT_DIR/info/exclude si existe.    --gitfile[=]archivo           Usa explícitamente el archivo indicado como archivo gitignore.    --ignore-case           Si se especifica un patrón con -P o -I, la coincidencia no tendrá           en cuenta mayúsculas y minúsculas.    --matchdirs           Aplica el patrón de -P también a los nombres de directorios.           Si un directorio coincide, se deshabilita la coincidencia en su           contenido. Si se usa --prune, los directorios vacíos que coincidan          no se eliminarán.    --metafirst           Imprime la información de metadatos al inicio de la línea en           lugar de después de las líneas de sangría.    --prune           Elimina los directorios vacíos de la salida. Útil junto con -P o           -I. Consulte ERRORES Y NOTAS más abajo.    --info           Imprime comentarios de archivos encontrados en archivos .info.    --infofile[=]archivo           Usa explícitamente el archivo indicado como archivo info.    --noreport           Omite el informe final de archivos y directorios.    --charset[=]charset           Define el conjunto de caracteres usado para la salida HTML y las           líneas gráficas.    --filelimit[=]#           No desciende a directorios que contengan más de # entradas.     --timefmt[=]formato           Imprime (implica -D) y formatea la fecha según el formato de           strftime(3).    -o archivo           Envía la salida al archivo indicado.``

### OPCIONES DE ARCHIVO

   ``-q     Imprime caracteres no imprimibles en los nombres como signos de           interrogación.    -N     Imprime los caracteres no imprimibles tal como están.    -Q     Coloca los nombres de archivo entre comillas dobles.    -p     Imprime el tipo de archivo y permisos (como `ls -l`).    -u     Imprime el nombre del usuario o el UID si no existe nombre.    -g     Imprime el nombre del grupo o el GID si no existe nombre.    -s     Imprime el tamaño de cada archivo en bytes.    -h     Imprime el tamaño de forma legible para humanos (K, M, G, T, P,           E).    --si   Igual que -h pero usando unidades SI (potencias de 1000).    --du   Para cada directorio, informa su tamaño como la suma de todos sus           archivos y subdirectorios. También se muestra el total usado al           final (como `du -c`). Implica -s.    -D     Imprime la fecha de la última modificación o, con -c, el último           cambio de estado.    -F     Añade `/` a directorios, `=` a sockets, `*` a ejecutables, `>`           a puertas (Solaris) y `|` a FIFO, como `ls -F`.    --inodes           Imprime el número de inodo del archivo o directorio.    --device           Imprime el número de dispositivo al que pertenece.``

### OPCIONES DE ORDENAMIENTO

   `-v     Ordena por versión.    -t     Ordena por última modificación.    -c     Ordena por último cambio de estado.    -U     No ordena; usa el orden del directorio.    -r     Orden inverso.   --dirsfirst           Muestra primero los directorios.   --filesfirst           Muestra primero los archivos.   --sort[=]tipo           Ordena por tipo: ctime, mtime, size o version.`

### OPCIONES GRÁFICAS

   `-i     No imprime líneas de sangría.    -A     Activa gráficos de línea ANSI.    -S     Usa gráficos CP437.    -n     Desactiva siempre los colores.    -C     Activa siempre los colores.`

### OPCIONES XML/JSON/HTML

   `-X     Salida en formato XML.    -J     Salida en formato JSON.    -H baseHREF           Activa salida HTML con referencias HTTP.   --hintro[=]archivo           Usa el archivo como introducción HTML.   --houtro[=]archivo           Usa el archivo como cierre HTML.    -T título           Define el título y encabezado H1 en HTML.   --nolinks           Desactiva los hipervínculos en HTML.`

### OPCIONES DE ENTRADA

   `--fromfile           Lee un listado desde un archivo en lugar del sistema de archivos.   --fromtabfile           Lee un árbol desde un archivo con sangría por tabulaciones.   --fflinks           Procesa información de enlaces simbólicos desde un archivo.`

### OPCIONES MISCELÁNEAS

   `--help           Muestra ayuda detallada.   --version           Muestra la versión de tree.    --           Fin del procesamiento de opciones.`

## ARCHIVOS .INFO

   `Los archivos .info son similares a .gitignore. Contienen comentarios o    patrones comodín y permiten asociar comentarios a archivos coincidentes.`

## ARCHIVOS

   `/etc/DIR_COLORS    ~/.dircolors    .gitignore   $GIT_DIR/info/exclude    .info    /usr/share/finfo/global_info`

## ENTORNO

   `LS_COLORS, TREE_COLORS, TREE_CHARSET, CLICOLOR, CLICOLOR_FORCE, NO_COLOR,    LC_CTYPE, LC_TIME, TZ, STDDATA_FD`

## AUTOR

   `Steve Baker    Salida HTML por Francesc Rocher    Conjuntos de caracteres y soporte OS/2 por Kyosuke Tokoro`

## ERRORES Y NOTAS

   `Tree no elimina directorios vacíos con -P y -I por defecto.    Las opciones -h y --si redondean al número entero más cercano.    Algunas combinaciones pueden producir conteos incorrectos.   --prune y --du cargan todo el árbol en memoria.    Los árboles XML/JSON no tienen colores.    Probablemente haya más.`

## VER TAMBIÉN

   `dircolors(1), ls(1), find(1), du(1), strftime(3), gitignore(5)`

**Tree 2.1.1** **TREE(1)**
