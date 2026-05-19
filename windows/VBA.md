# VBA

**VBA** (Visual Basic for Applications) es el lenguaje de programación orientado a objetos que vive "detrás" de los programas de Microsoft Office, como Excel, Word y Access.

Su función principal es la **automatización**. En lugar de realizar tareas repetitivas manualmente, puedes escribir un código (o grabar una "macro") para que la computadora lo haga por ti en segundos.

## VBA OBJETOS

Para acceder a estos objetos utilizamos el operador `.` y su jerarquía.

* Propiedades = características del objeto. 
  En el editor se representan con un símbolo gris.
* Métodos = funciones del objeto. 
  En el editor se representan con un símbolo verde.
* Colecciones = Grupo de objetos de la misma clase, cuando veamos una palabra en plural como `worksheets` se refiere a una colección, la palabra `worksheet` se refiere al objeto individual.
* [Jerarquía](https://learn.microsoft.com/en-us/office/vba/api/overview/excel/object-model) = Es la herencia de un padre ej:

  * application > workbooks > worksheets > ...

  Podemos saltar algunos objetos, esto por medio del objeto activo.

  

## EDITOR VBA

VBA maneja su propio editor, el cual podemos abrir con la combinación de teclas `alt + F11` o desde la pestaña programador.

:round_pushpin: **MODULOS**

Los módulos en VBA son contenedores y ordenadores de código. estos contienen procedimientos. `End Nombre() End Sub` se pueden crear de forma manual o con la pestaña insertar > procedimiento

* Crear modulo: (Raíz del proyecto > Insertar > Modulo | Pestaña insertar > Modulo).

:round_pushpin: **COMENTARIOS**

* Línea: Estos se crean con el carácter `' Comentario`
* Bloque: (Ver > Barra de herramientas > Edición) seleccionar bloque con comentario para comentar bloque y para quitar comentario de bloque seleccionar bloque sin comentario.  

:round_pushpin: **CONCATENAR**

`&` Nos permite concatenar cadena de caracteres.

## TIPOS DE DATOS

| Tipo de dato        | Tamaño               | Rango / Descripción                                  |
| ------------------- | -------------------- | ---------------------------------------------------- |
| `Byte`              | 1 byte               | 0 a 255                                              |
| `Boolean`           | 2 bytes              | `True` o `False`                                     |
| `Integer`           | 2 bytes              | -32,768 a 32,767                                     |
| `Long`              | 4 bytes              | -2,147,483,648 a 2,147,483,647                       |
| `LongLong`          | 8 bytes              | (Solo en sistemas de 64 bits)                        |
| `Single`            | 4 bytes              | Números decimales de precisión simple                |
| `Double`            | 8 bytes              | Números decimales de doble precisión                 |
| `Currency`          | 8 bytes              | -922,337,203,685,477.5808 a 922,337,203,685,477.5807 |
| `Decimal`           | 14 bytes             | Alta precisión (usado como subtipo de `Variant`)     |
| `Date`              | 8 bytes              | Fechas desde 1/1/100 hasta 31/12/9999                |
| `String` (fijo)     | Depende              | Longitud fija definida                               |
| `String` (variable) | Depende              | Hasta ~2 mil millones de caracteres                  |
| `Object`            | 4 bytes (referencia) | Referencia a objetos                                 |
| `Variant`           | 16 bytes             | Puede contener cualquier tipo de dato                |
| `User-defined`      | Depende              | Estructuras definidas con `Type`                     |

### VARIABLES

Para la declaración de una variable utilizamos `Dim [Nombre] As [TipoDato]` . También podemos realizar declaraciones múltiples en una sola línea: `Dim [nombre] As [TipoDato], [nombre] As [TipoDato]`.

* No pueden llevar espacios en blanco.
* El nombre puede contener hasta 255 caracteres.
* No puede comenzar con numero o caracteres especiales.
* Cuando no especificamos un tipo de dato el tipo por defecto es **Variant**.

  * Cuando creamos una variable y asignamos valor si haber declarado esta, el valor por defecto es Variant. `nombre = "Jefferson"`
  * Cuando agregamos un dato con `Set` sin haber declarado la variable esto se puede hacer, pero tener en cuenta que el valor por defecto será Variant, no es recomendado asignar valores sin haber declarado el tipo de dato.

* Se pueden asignar varios valores en una misma línea solo que separados por `:` :bulb: `nombre = "Jefferson": edad = 26`

  :warning: Los tipos de dato Objeto requieren de la palabra clave `set nomVar = Objeto`.

### CONSTANTES

Se utilizan para almacenar un valor fijo, para un uso posterior. Por lo regular estas constantes se declaran a nivel de modulo o publicas y se inicializan junto a su declaración de lo contrario nos daría error.

:key: **Sintaxis:** `Const [NomConstante] As [TipoDato] = [Valor]`

### ÁMBITO DE VARIABLES

Es como decir la variable donde funciona, donde tiene su ámbito.

**Ámbitos**:

* **Local**: 

  * A nivel de procedimiento: Esta variable solo funciona desde la apertura del procedimiento hasta el final de este.

    ```vb
    End LocalProcedimiento()
    	Dim nombre As String
    	nombre = "Jefferson"
    	MsgBox nombre
    End Sub
    ```

  * A nivel de modulo: Disponible para cualquier procedimiento pero dentro del mismo modulo.

    ```vb
    ' Para esto debemos declarar la variable fuera de cualquier 
    ' procedimiento, importante, se pueden declarar fuera pero no
    ' inicializar fuera de este.
    
    Dim nombre As String
    
    Sub LocalModulo()
        nombre = "Jefferson" ' Variable inicializada
        MsgBox nombre
    End Sub
    
    Sub OtroProcedimiento()
        MsgBox nombre ' No funcionaria dado a que no se a inicializado
    End Sub
    ```

  * publica: visible desde cualquier modulo y/o procedimiento.

    ```vb
    ' Esta se declara fuera de cualquier procedimiento
    ' Con la palabra clave <public>
    
    Modulo1
    Public nombre As String
    
    Sub VarPublica()
    	' Esta iniciacion queda para este procedimiento.
    	nombre = "Jefferson"
    End Sub
    
    Modulo2
    Sub LlamarVarPublica()
    	Call VarPublica
    	' Se debe incializar la variable para este procedimiento.
    	nombre = "Andrea"
    	MsgBox nombre
    End Sub
    ```

## MATRICES

Las matrices nos permiten almacenar datos en posiciones, estas pueden ser de una o varias dimensiones.

:key: **Sintaxis:**

* `Dim nombre_matriz(numerodeespacios) As TipoDatoqueAlmacenara`

Podemos indicarle desde donde comenzar hasta donde ir

* `Dim nombre_matriz(desde To hasta) As TipoDat`

:bulb: **Almacenar datos en el interior**

* `nombre_matriz(posición) = "valor"` 



## BUCLES

`For Next` Este bucle repite algo un número exacto de veces.

```vb
' Conocemos cuántas veces repetir
Sub MiBucle()

	Dim i As Integer
	
	For i = 1 To 5
		Cells(i, 1).Value = "Hola " & i
	Next i

End Sub
```

`Do While` Este se repite mientras una condición sea verdades. Es como decir: *Sigue haciendo esto MIENTRAS se cumpla esta condición*

```vb
' Repite hasta que algo cambie
Sub MiBucleWhile()

	Dim i As Integer
    i = 1 ' Inicializamos iterador
	
    Do While i <= 5 ' Repite mientras i sea menor o igual a 5.
		Cells(i, 1).Value = "Fila " & i
        i = i + 1 ' Le suma 1 a i en cada vuelta.
    Loop ' Regresa al inicio del bucle.

End Sub
```

`For Each` Este recorre cada celda de un rango automáticamente.

```vb
' Recorrer celdas o lista
Sub MiBucleForEach()
    
    Dim celda As Range
    
    For Each celda In Range("A1:A5")
	    celda.Value = " Revisado"
    Next celda

End Sub
```



## OBJETOS PREDEFINIDOS

* `Range()` nos permite seleccionar una celda o un rango de celdas, también cuenta con una propiedad por defecto que es `.value = <valor>`.

## FUNCIONES PREDEFINIDAS

* `MsgBox "mensaje"`: Lanza una caja con un mensaje.