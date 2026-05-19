# POWERSHELL

Línea/interfaz de comandos que permite digitar instrucciones para que haga algo.

## VARIABLES DE ENTORNO

Las variables de entorno son como una lista de "notas adhesivas"que el sistema operativo tiene a mano para recordar datos importantes mientras trabaja.

En lugar de que cada programa tenga que adivinar dónde están las cosas, simplemente le pregunta al sistema "Oye, ¿dónde está tal cosa?", y el sistema responde leyendo esa variable.

:key: `$env:` Busca en las variables de entorno

En Powershell se utiliza el signo `$` para indicar que es una variable y se utiliza el prefijo `env` para indicar que son variables de entorno esto dado que Powershell utiliza algo llamado PSDrive (unidades de disco de PowerShell), los `:` se utilizan como un separador de unidad, es como decir "Entra en este almacén".

```powershell
# Variables de entorno del usuario.
[Environment]::GetEnvironmentVariables("User")

# Variables de entorno del sistema.
[Environment]::GetEnvironmentVariables("Machine")

# Otra forma de ver las variables de entorno pero con interfaz
rundll32.exe sysdm.cpl,EditEnvironmentVariables

# Listar todos los argumentos disponibles
Get-ChildItem env:

# Obtner el contenido de una variable de entorno
Write-Output $env:path

# Operador -split "separarpor"
Write-Output ($env:path -split ";")

# 1. Obtenemos el PATH actual del registro, 
# Se puede cambiar por Machine que son las del sistema.
$viejoPath = [Environment]::GetEnvironmentVariable("Path", "User")

# 2. Creamos el nuevo PATH sumando la carpeta nueva
$nuevoPath = $viejoPath + ";C:\Tu\Nueva\Ruta"

# 3. Lo guardamos de vuelta
[Environment]::SetEnvironmentVariable("Path", $nuevoPath, "User")
```

*Crear variables de entorno:*

Importante al utilizar este método no utilizar el nombre de una variable existente o este sobrescribe todo lo existente.

1. Crear una variable temporal (se borra al cerrar la consola):
   [`set NOMBRE_VARIABLE=holamundo`] `write-output $env:nom_var`
2. Crear una variable permanente para el usuario:
   [`setx NOMBRE_VARIABLE "C:\mi\ruta"`] `write-output $env:nom_var`
   3 Crear una variable permanente para el sistema y disponible para todo usuario:
   [`setx NOMBRE_VARIABLE "C:\mi\ruta" /M`] `write-output $env:nom_var`, /M -> para todo el sistema.

## POLITICAS DE SEGURIDAD

Nos permite definir que tipo de scripts pueden ejecutarse.

***execution policy:***

El comando `get-executionpolicy -list` nos permite visualizar las políticas establecidas en cada nivel, de igual forma podremos visualizar la política de seguridad que se encuentra establecida actualmente y a que nivel corresponde mediante  `get-executionpolicy`.

:key: *ESTABLECER UNA POLITCA DE SEGURIDAD:*

`set-executionpolicy -executionpolicy <valor> -scope <valor>`

:unlock: *DONDE:*

`-ExecutionPolicy <valor>` Define la regla de seguridad para la ejecución de scripts.

Valores del parámetro:

* `Restricted` Valor por defecto en Windows 10/11. No permite la ejecución de ningún script; solo comando individuales en la consola.
* `RemoteSigned` Valor por defecto en Windows Server. Permite scripts locales sin firma, pero exige que los descargados de internet estén firmados por un editor de confianza.
* `AllSigned` Solo permite ejecutar scripts firmados por un editor de confianza, incluidos los que escribas tú mismo en tu equipo.
* `Unrestricted` Permite todos los scripts. Si el script es de internet y no esta firmado, mostrara una advertencia antes de ejecutarlo.
* `Bypass` Nada se bloquea y no hay advertencias ni mensajes. Se utiliza principalmente para automatizaciones integradas donde la seguridad se gestiona externamente.
* `Undefined` Indica que no hay política definida para ese ámbito especifico, si todos los ámbitos son `undefined`, se aplica la política por defecto (`restricted`).

`-scope <valor>` Le indica a PowerShell a quién o a qué nivel debe aplicarse esa regla de seguridad.

Valores del parámetro:

- `Process` Solo afecta a la sesión actual de PowerShell. Al cerrar la ventana, el cambio se pierde.
- `CurrentUser` Afecta solo al usuario que inicio sesión, Se guarda en el registro del usuario.
- `LocalMachine` Afecta a todos los usuarios del equipo. Requiere permisos de administrador para cambiarse.
- `UserPolicy / MachinePolicy` Establecidos mediante directivas de grupo (GPO). Estos **no pueden ser sobrescritos** por comando locales.

:bulb: *EJEMPLO:*

`set-executionpolicy -executionpolicy RemoteSignet -Scope Process`

## INSTALAR POWERSHELL

Como aprendimos en la sesión anterior este se puede instalar con `winget` | `winget install --id Microsoft.PowerShell`

## GESTOR DE PAQUETES

`winget` Es el administrador de paquetes oficial de Windows 10 y 11. Sirve para instalar aplicaciones completas (Chrome, Steam, VS Code, etc.) directamente desde la consola.

- `winget --help` Nos permite ver una guía completa de los comandos disponibles.
- `winget search|find <appname>` Nos permite buscar una aplicación y ver si esta esta disponible.
  - `winget find --query|q ""` Permite listar todos los paquetes disponibles.
- `winget install <appname_id>` Nos permite instalar la aplicación, tener encentra que este se instala con el id.
- `winget [list|ls]` Nos muestra una lista de todos los programas instalados en nuestro sistema.
  - `winget [list|ls] --name <appname>` Lista las aplicaciones la coincidencia de nombre dado.
  - `winget [list|ls] --name <appname> --details` Muestra los detalles de una aplicaciones.
- `winget show --name|id <appname|id>` Muestra los detalles de una aplicación especifica como sus metadatos de origen y asociados.
- `winget upgrade` Lista todas la aplicaciones con actualización disponible.
  - `winget upgrade --all` Actualiza todas la aplicaciones disponibles en actualización.
  - `winget upgrade --name|id` Permite actualizar una aplicación especifica por nombre o por identificador.
  - `winget upgrade <appname> <appname>` Permite actualizar varias aplicaciones a la ves.
- `winget [uninstall|remove|rm] --name|id <appname|id>` Desinstala una aplicación especifica.
  - Podemos utilizar el atributo `--purge` Este elimina todos los archivos y directorios del paquete (portable)

- `winget [repair|fix] --name|id <appname|id>` Funciona para reparar una aplicación que tenga problemas o archivos dañados.

## SCRIPT

- Estos llevan la extension `.ps1`.
- Un script no se puede ejecutar con doble click, para ejecutar este debemos hacerlos desde el powershell `.\ruta_archivo`.
  - :bulb: **Solución**: Podemos crear un archivo .bat que ejecute este archivo mediante la siguiente instrucción `powershell -ExecutionPolicy Bypass -File "C:\ruta\script.ps1`.
  - :unlock: **Desglose:**
    `powershell` Programa a utilizar, en este caso powershell.
    `-ExecutionPolicy` Parámetro del programa powershell este define como se permite ejecutar un script.
    `-Bypass` Este es el valor del parámetro anterior.
    `-File` Indica que ejecutara un archivo no un comando escrito a mano.
    `C:\ruta\script.ps1` La ubicación del script.

## LENGUAJE

### COMENTARIOS

- LÍnea:
  `# texto` Esto crea un comentario de lÍnea.
- Bloque: 
  `<# texto #>` Esto crea un comentario de bloque.

### VARIABLES

En Powershell todas la variables empiezan con el símbolo de `$`

`$nombre = "Jefferson"` imprimimos el contenido `write-output $nombre`

*Tipos de datos:*

| Tipo            | Nombre técnico | Ejemplo      |
| --------------- | -------------- | ------------ |
| Texto           | String         | "Hola"       |
| Numero entero   | Int32          | 42           |
| Numero decimal  | Double         | 3.14         |
| Verdadero/Falso | Boolean        | $true/$false |
| Fecha           | DateTime       | Get-Date     |
| Lista           | Array          | @(1,2,3)     |

 *Casting / conversión de tipos:*

Pasar de un tipo de dato a otro, sintaxis: `$fecha_nacimiento = [DateTime]"2026-11-17"`

### CONDICIONES

:key: ***if***

```powershell
if (condicion) {
	# si
} elseif(condicion) {
	# sino si
} else {
	# sino
}
```

*Operadores de comparación:*

| Operador             | Significado                                 | Ejemplo        |
| -------------------- | ------------------------------------------- | -------------- |
| -eq (equal)          | Igual a                                     | $x -eq 10      |
| -ne (not equal)      | No igual a                                  | $x -ne 10      |
| -gt (great than)     | Mayor que                                   | $x -gt 5       |
| -lt (less than)      | Menor que                                   | $x -lt 5       |
| -ge (great or equal) | Mayor o igual que                           | $x -ge 18      |
| -le (less or equal)  | Menor o igual que                           | $x -le 100     |
| -match, -notmatch    | Compara un texto con una expresión regular. | -match "^\d+$" |

*Operadores lógicos:*

| Operador | Significado | ¿Cuando es verdadero?             |
| -------- | ----------- | --------------------------------- |
| -and     | Y           | Cuando ambas son verdaderas.      |
| -or      | O           | Cuando al menos una es verdadera. |
| -not     | No          | Invierte el resultado.            |

*Operador de pertenencia:*

| Operador    | Significado                                    | Ejemplo        |
| ----------- | ---------------------------------------------- | -------------- |
| -in, -notin | Valida si un elemento se encuentra en la lista | dato -in array |
|             |                                                |                |

:key: ***switch***

Cuando tenemos muchas opciones posibles, en lugar de escribir muchos elseif, usamos switch. Es más limpio y ordenado.

```powershell
switch (valorevaluado) {
	<# 
	Debemos utilizar 'break' en caso de que se cumpla una
	condicion de lo contrario evaluara todo.
	#> 
	"valor" {#cumple; break} 
	<# 
	Se pueden evaluar condiciones mas grandes, y hacemos referencia
	A la variable evaulada mediante el siguiente simbolo '$_' de esta
	forma estamos indicando que queremo evaluar la variable
	valorevaluado.
	#>
	{ $_ -gt 0 -and $_ -le 15 } {#cumple; break}
	<#
	Podemo crear un valor por default en caso de que ninguna
	condicion sea verdadera.
	#>
	default {#valor ; break}
}
```

:warning: *Importante*

El uso de `break` o `continue` esta reservado específicamente para bucles o en el caso de `switch` solo `break` y si queremos utilizar `continue` dentro de un if, este deberá estar dentro de un bucle ya que le dirá al bucle que salte a la siguiente iteración.

### BUCLES

:key: ***for,*** utilizamos este cuando conocemos cuantas veces repetir.

```powershell
# incremento ++ o decremento --
for (inicio; condicion; incremento) {
	# Lo que se repite
}

# EJEMPLO
for ($i = 1; $i -le 10; $i++) {
	Write-Output "Recogi el juguete número $i"
}
```

:key: ***while,*** Mientras algo sea verdadero "Mientras tengas hambre, sigue comiendo".

```powershell
$finalizador = 0
while (condicion) {
	# Lo que se repite
	$finalizador incremento/decremento
}

# EJEMPLO
$hambre = 5
while ($hambre -ge 1) {
	Write-Output "Hola Mundo"
	$hambre--
}
```

:key: ***do while,*** Al menos una vez, luego mientras sea verdad.

Este permite ejecutar lo que se repite una vez antes de entrar a evaluar.

```powershell
# Tambien requere de un finalizador, lo mismo que el while
$finalizado = 0

do {
	# lo que se repite y se ejecuta una sola ves.
	$finalizado incremento/decremento
} while (condicion)

# EJEMPLO
$intento = 0

do {
	Write-Output "Intentando conectar..."
	$intento++
} ($intento -lt 3)

Write-Output "Intentos realizado: $intento"
```

:key: ***foreach,*** por cada elemento de una lista/array

```powershell
foreach (elemento in lista) {
	# Lo que se hace con cada elemento
}

# EJEMPLO
$frutas = @("Manzana", "Pera", "Uva")

foreach ($fruta in $frutas) {
	Write-Output "Me comi una $fruta"
}
```

### FUNCIONES

```powershell
function nombre_funcion {
	param (
		$nombre_parametro,
		$nombre_parametro,
		$nombre_parametro = "valor por defecto."
	)
	# Lo que hace la funcion
	return $resultado # devolver un resultado.
}

# Llamada de la funcion, si tiene un valor por defecto
# no es necesario llamar el parametro.
nombre_funcion -nombre_parametro valor -nombre_parametro "valor"
```

### ANSI

Son códigos especiales que le indica a la consola como mostrar el texto.

```powershell
# Sintaxis
# `e[color;stilo;R;G;Bm texto `e[0m
# esto se pueden guardar en variables para no repetir codigo
```

:old_key: Tabla de codigos:

| Código                    | Efecto                                          |
| ------------------------- | ----------------------------------------------- |
| 0                         | Reset -Vuelve normal                            |
| 1                         | Negrita                                         |
| 2                         | Tenue                                           |
| 3                         | Cursiva                                         |
| 4                         | Subrayado                                       |
| 5                         | Parpadeando                                     |
| 7                         | Invertido                                       |
| 9                         | Tachado                                         |
| 30-37                     | Colores de texto                                |
| 40-47                     | Colores de fondo                                |
| 90-97                     | Colores brillantes de texto                     |
| 100-107                   | Colores brillantes de fondo                     |
| estilo;estilo;38;2;R;G;Bm | Cambia el color del texto por uno personalizado |
| estilo;estilo;48;2;R;G;Bm | Cambia el color del fondo por uno personalizad  |

:old_key: Posición del cursor:

| Código            | Efecto                                                       |
| ----------------- | ------------------------------------------------------------ |
| e[nfila;ncolumnaH | Imprimir contando desde la primera impresión en pantalla, es decir cuenta las filas de arriba abajo y las espacios(columnas) de izquierda a derecha, tener cuidado porque esto elimina lo que se encuentre después de donde se ubico el cursor. |
| e[nlineasN        | Se encarga de subir el cursor, contando desde la linea anterior. |
| e[nlieasB         | Se encarga de bajar cierta cantidad de lineas depues de el prompt y imprime una despues. |
| e[2               | se encarga de limpiar la pantalla, tener en cuenta que esto solo da saltos en blanco mas no hace un clear, por lo tanto se puede ver la información anterior realizando scroll. |



## COMANDOS

- Imprimir un mensaje en shell:
  - Forma larga:
    - `write-output "texto"` Se puede capturar salida.
    - `write-host "text"` No se puede capturar salida.
  - Forma corta:
    Se pueden ver como los alias de un comando largo.
    - `[echo|write] "texto"` Imprime en pantalla.
- Imprimir bloques de texto (here-strings), Imporatnte no dejar saltos de linea después de @ o antes @.
  - `$var = @" "@` Con las comillas dobles podemos introducir variables y caracteres especiales, los cuales pueden ser interpretados.
  - `@var = @' '@` Con la comilla simple, todo es interpretado como texto.
- Identificar si estamos ejecutando un comando externo o comando interno
  - `get-command <comando>` si este tiene algo como aplicación .exe .com .bat es un comando externo, de lo contrario es interno del powershell.
- Obtener propiedades, métodos y otros de un comando.
  - `comando | [get-member|gm]`
- Para obtener la ayuda de comandos externos
  - `comando --help`
  - `comando /?`



## REGEX

Expresiones regulares.
