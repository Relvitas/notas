# CMD

Como se suele denominar a esta ventana:

* Linea/Interfaz de comandos.
* Símbolo del sistema.
* Procesador de comandos.
* Shell del sistema.
* Consola de windows.
* Interprete de comandos.
* Terminal.

## :pushpin: DICCIONARIO

* `\` el backslash nos permite acceder a directorios.
* `parámetro` Funcionalidad extra que trae un comando.
* `variables de entorno` Son variables que el sistema operativo guarda para que los programas sepan como comportares son como variables globales del sistema.
* `"comillas"` Se utiliza para cuando un nombre tiene espacios en blanco, también para rutas.

## :round_pushpin: COMANDOS

* `help` proporciona una ayuda de los comandos disponibles.
  * `help [comando]` muestra una ayuda de un comando especifico.
  * `[comando] /?` Esta es otra forma de obtener ayuda de un comando.
  * `[comando /?]| more` Si un comando no muestra información es posible algún error, y podemos mostrar este paso a paso.
* `cd` (change directory) nos permite cambiar de directorio o mostrar la ruta actual en donde nos encontramos ubicados.
  * `chdir` es una función no un comando que nos permite también cambiar de directorio.
  * `.\` Directorio actual.
  * `\` Acceder a.
  * `..` Regresar.
* `md` (make directory) nos permite crear un directorio.
* Renombrar un archivo/carpeta:
  
    | alias | comando |argumentos                             |
    |-------|---------|---------------------------------------|
    |`ren`  |`rename` |[nombre_archivo_carpeta] [nuevo nombre]|

* `cls` (clean screen) este comando limpia la linea de comandos.
* `attrib` Muestra o cambia los atributos de un archivo, podemos ver esto como los modificadores de acceso.
  * Parámetros:
    * `+` Agregar atributo.
    * `-` Quitar atributo.
    * `/s` aplica a todos los archivos dentro y sub carpetas.
    * `/d` incluye también carpetas no solo archivos.
* `dir` Muestra una lista de archivos y sub directorios en un directorio.
* `path` Es una variable de entorno de windows que le dice al sistema donde buscar los programas cuando escribimos un comando.
  * `path ruta;%path%`
  `ruta` Dirección donde se encuentra el ejecutable.
  `%path%` Mantiene los que ya existen.
  Ejemplo: `path C:\Users\jefferson\desktop;%path%` Esto agrega un nuevo path en la sesión actual del CMD, es decir no es permanente.
  * Si queremos agregar las rutas de forma permanente:
    * Agregar al path del usuario `setx PATH "%PATH%;C:\mi\ruta"`
    * Agregar al path del sistema (requiere cmd administrador) `setx /M PATH "%PATH%;C:\mi\ruta"`
* `rd` Elimina un directorio.
  * `/s` Elimina sus subdirectorios y archivos.
  * `/q` No solicita confirmación.
  * `echo` Permite imprimir en pantalla
    * `echo.` Imprime un salto de linea.
  * `set nom_variable=valor`
  * `()` Ejecuta todo lo que se encuentra dentro "se puede capturar la salida".
  * `>` Redirige la salida y remplaza todo.
  * `>>` Redirige la salida sin afectar el archivo existente.
  * **COMENTARIOS**:
    * `REM` Se utiliza para explicar cosas.
    * `::` Mas general se utiliza para títulos.

## OPERADORES

:round_pushpin: De comparación:

| Operador | Significado     | Ejemplo            |
| -------- | --------------- | ------------------ |
| `==`     | Igual           | `if "%a%"=="hola"` |
| `EQU`    | Igual (números) | `if 5 EQU 5`       |
| `NEQ`    | Diferente       | `if 5 NEQ 3`       |
| `LSS`    | Menor que       | `if 3 LSS 5`       |
| `LEQ`    | Menor o igual   | `if 5 LEQ 5`       |
| `GTR`    | Mayor que       | `if 10 GTR 5`      |
| `GEQ`    | Mayor o igual   | `if 5 GEQ 5`       |

:round_pushpin: Especiales

| Comando      | Significado                        | Ejemplo                    |
| ------------ | ---------------------------------- | -------------------------- |
| `exist`      | Verifica si existe archivo/carpeta | `if exist archivo.txt`     |
| `not`        | Negación                           | `if not exist archivo.txt` |
| `defined`    | Variable definida                  | `if defined var`           |
| `errorlevel` | Código de error                    | `if errorlevel 1`          |

:round_pushpin: Lógicos:

| Operador | Nombre | Descripción | Ejemplo |
|----------|--------|-------------|---------|
|`&&`| AND | Ejecuta el siguiente comando si el anterior fue exitoso | `dir && echo OK` |
| `\|\|` | OR | Ejecuta el siguiente comando si el anterior falla | `dir archivo.txt \|\| echo Error` |
| `\|` | PIPE | Pasa la salida de un comando a otro | `dir \| more` |

:round_pushpin: Matemáticos:

| Operador | Significado    | Ejemplo         |
| -------- | -------------- | --------------- |
| `+`      | Suma           | `set /a x=5+3`  |
| `-`      | Resta          | `set /a x=5-2`  |
| `*`      | Multiplicación | `set /a x=5*2`  |
| `/`      | División       | `set /a x=10/2` |
| `%`      | Módulo         | `set /a x=10%3` |

:round_pushpin: Avanzados:

| Operador | Significado           | Ejemplo       |
| -------- | --------------------- | ------------- |
| `+=`     | Sumar y asignar       | `set /a x+=1` |
| `-=`     | Restar y asignar      | `set /a x-=1` |
| `*=`     | Multiplicar y asignar | `set /a x*=2` |
| `/=`     | Dividir y asignar     | `set /a x/=2` |
| `%=`     | Módulo y asignar      | `set /a x%=2` |

:round_pushpin: Bits (nivel pro)

| Operador | Significado         | Ejemplo         |
| -------- | ------------------- | --------------- |
| `&`      | AND bit a bit       | `set /a x=5&3`  |
| `\|`     |     OR bit a bit    |`set /a x=5 \| 3`|
| `^`      | XOR                 | `set /a x=5^3`  |
| `<<`     | Desplazar izquierda | `set /a x=1<<2` |
| `>>`     | Desplazar derecha   | `set /a x=4>>1` |

## :round_pushpin: ATAJOS DE TECLADO

* `Alt + Enter` Este atajo proporciona un CMD en pantalla completa.

## :round_pushpin: VARIABLES DE ENTORNO

* Conocer el nombre del equipo [`%computername%`, `%logonserver%`, `%serdomain%`].
* Conocer el nombre de usuario del sistema [`%username%`]
* Dirección de la carpeta personal del usuario [`%userprofile%`]
* Donde se guardan los datos de las aplicaciones [`%appdata%`]
* Carpetas donde se instalan los programas [`%programdata%`, `%programfiles%`]
* Ruta del cmd [`%comspec%`]
* fecha actual [`%date%`]
* hora actual [`%time%`]
* devolver la unidad del sistema [`systemdrive`]
* dirección del directorio de windows [`%systemroot%`, `%windir%`]

:bulb: **Crear nuestras propias variables de entorno**:
Recordemos que las variables de entorno son valores que el sistema operativo guarda para que los programas sepan como comportarse.

* Configurar programas (Python, Java, etc.).
* Guardar rutas importantes.
* Controlar comportamiento del sistema.
* Compartir información entre procesos.

1. Crear una variable temporal (se borra al cerrar la consola):
[`set MI_VARIABLE=holamundo`] `echo %MI_VARIABLE%`
2. Crear una variable permanente para el usuario:
[`setx RUTA_PROYECTO "C:\mi\ruta"`] `echo %RUTA_PROYECTO%`
3 Crear una variable permanente para el sistema y disponible para todo usuario:
[`setx RUTA_PROYECTO "C:\mi\ruta" /M`] `echo %RUTA_PROYECTO%`, /M -> para todo el sistema.