## COMENTARIOS

:fire: docstring

```python
# Se colocan al inicio del archivo para describir su propósito.
""" 
Este módulo contiene funciones matemáticas básicas.
Autor: Juan Pérez
Fecha: 2025-02-26
"""

# Se colocan dentro de una funcion u/metodo
def multiplicar(a, b):
    """
    Multiplica dos números y devuelve el resultado.

    Parámetros:
    a (int, float): Primer número.
    b (int, float): Segundo número.

    Retorna:
    int, float: Resultado de la multiplicación.
    """
    return a * b


# Se colocan dentro de la clase para explicar su propósito.
class Persona:
    """Clase que representa una persona con nombre y edad."""

    def __init__(self, nombre, edad):
        """Inicializa una persona con nombre y edad."""
        self.nombre = nombre
        self.edad = edad

    def saludar(self):
        """Devuelve un saludo personalizado."""
        return f"Hola, soy {self.nombre}."

print(Persona.__doc__)  # Muestra la descripción de la clase
print(Persona.saludar.__doc__)  # Muestra la descripción del método
```

:fire: Comentario de linea

Un **comentario de línea** en Python se escribe usando el símbolo `#`, se utilizan para comentar lineas de codigo.

```python
print("Hola, mundo")  # Esto imprime un mensaje en pantalla
```

## DECLARACION DE VARIABLE

:fire: Sintaxis:

```python
identificador = 'valor'
```

:fire: Variable tipo local

```python
def local_function():
    x = 10 # variable local
    print(f'El valor de la variable es {x}')

print(x) # genera error dado a que es una variable local
```

:round_pushpin: nonlocal

La palabra clave **`nonlocal`** se usa dentro de una función anidada para indicar que una variable pertenece a un **ámbito superior (pero no global)**.

```python
'''
    Es útil cuando queremos modificar una variable 
    de una función externa sin afectar la variable global.
'''
def externa():
    x = 10  # Variable en el ámbito externo

    def interna():
        nonlocal x  # Modificamos la variable de `externa`
        x = 20
        print("Dentro de interna:", x)

    interna()
    print("Dentro de externa:", x)

externa()
# Dentro de interna: 20
# Dentro de externa: 20
```

:fire: Variable global

```python
x = 100

def nom_funcion():
    x = 10

print(x) #100
```

:round_pushpin: global

La palabra clave **`global`** se usa dentro de una función para indicar que una variable pertenece al **ámbito global**, en lugar de ser una variable local.

```python
contador = 0  # Variable global

def incrementar():
    global contador  # Indicamos que usaremos la variable global
    contador += 1  # Ahora sí podemos modificarla
    print(contador)

incrementar()  # Salida: 1
incrementar()  # Salida: 2
ntar()
```

:fire: Direnccion de memoria

```python
- id(nomVariable), regresa la posición de memoria
```

:fire: Hint -> pista o indicación de lo que almacena una variable

```python
- nomVariable: tipoDato = 'valor'
  -- nombre: str = 'Jefferson'
```

:fire: Conocer el tipo de dato

```python
- type(nomVariable)
  -- print(type(nombre))
```

:fire: Asignar un valor null

```python
- nomVar = None
    -- nombre = None -> esto indica que está vacía
```

:fire: conoser la longitud de una cadena

```python
len(var)
```

---

## TIPOS DE DATOS

Python es un lenguaje de programacion orientado a objetos. por tal motivo, son clases las que almacenan informacion.

| Tipo de Dato | Clase en Python | Descripción                                                                     |
| ------------ | --------------- | ------------------------------------------------------------------------------- |
| Entero       | `int`           | Números enteros, positivos o negativos, sin parte decimal. Ejemplo: `42`, `-3`. |
| Flotante     | `float`         | Números con parte decimal. Ejemplo: `3.14`, `-0.001`.                           |
| Complejo     | `complex`       | Números complejos con parte real e imaginaria. Ejemplo: `3 + 4j`.               |
| Cadena       | `str`           | Texto o secuencia de caracteres. Ejemplo: `"Hola, mundo"`.                      |
| Booleano     | `bool`          | Valores de verdad: `True` o `False`.                                            |
| Lista        | `list`          | Secuencia ordenada y mutable de elementos. Ejemplo: `[1, 2, 3]`.                |
| Tupla        | `tuple`         | Secuencia ordenada e inmutable de elementos. Ejemplo: `(1, 2, 3)`.              |
| Conjunto     | `set`           | Colección de elementos únicos y desordenados. Ejemplo: `{1, 2, 3}`.             |
| F. Conjunto  | `frozenset`     | Similar a `set`, pero inmutable. Ejemplo: `frozenset({1, 2, 3})`.               |
| Diccionario  | `dict`          | Colección de pares clave-valor. Ejemplo: `{"nombre": "Juan", "edad": 30}`.      |
| Rango        | `range`         | Secuencia inmutable de números. Ejemplo: `range(1, 10)`.                        |
| Binario      | `bytes`         | Secuencia inmutable de bytes. Ejemplo: `b"Hola"`.                               |
| Bytearray    | `bytearray`     | Similar a `bytes`, pero mutable.                                                |
| MemoriaView  | `memoryview`    | Permite acceder a datos binarios sin copiarlos.                                 |

> Cuando un numero es muy grande o muy pequeño se recomienda utilizar la notacion cientifica (a×10b):
> 
> ```python
> num1 = 5.3e6    # 5.3 × 10^6 → 5300000.0
> num2 = 4.2e-5   # 4.2 × 10^-5 → 0.000042
> ```

:round_pushpin: Ejemplos y explicaciones

```py
* LISTAS
Conjunto de elementos
    - indices
    - respeta orden de los elementos
    - mutable/modificable

Sintaxis:
    nomLista = [valor, 'valor']

- imprimir lista
    print(nomLista)

- acceder a elementos de manera individual
    print(nomLista[indice])

- acceder a elementos de manera inversa
    print(nomLista[-indice])

- acceder a un rango de elementos
    print(nomLista[indiceInicial:indiceFinal])
    tener en cuenta que el indiceFinal no se imprime, se
    imprime uno atrás.

- acceder desde el índice 0 sin incluir el índice final
    print(nomLista[:indiceFinal])

- acceder desde un índice inicial hasta el final
    print(nomLista[indiceInicial:])

- cambiar valor de índice
    nomLista[indice] = nuevoValor

- agregar un nuevo elemento, este se agrega al final de la lista
    nomLista.append('nuevoValor')

- insertar un elemento en un índice específico
    nomLista.insert(indice, 'valor')

- remover un elemento
    nomLista.remove(valorElemento)

- remover el último elemento de una lista
    nomLista.pop()

- eliminar un índice específico
    del nomLista[indice]

- limpiar/vaciar lista de elementos
    nomLista.clear()

- eliminar lista por completo esto incluye su declaración
    del nomLista

- iterar lista:
    for elemento in listaElementos:
        # cuerpo del ciclo
        print(elemento)

- obtener el largo de una lista
    len(nombreLista)

- Validar si un elemento está presente
    print('elemento' in nomLista)

* TUPLAS
    - respeta el orden de los elementos
    - inmutable/no modificable
    - si tiene solo un elemento este debe finalizar con (,)

Sintaxis:
    nomTupla = ('valor', valor)

Accesibilidad:
- Conocer el largo de una tupla
    len(nomTupla)

- acceder a un elemento
    nomTupla[indice]

- acceder a elementos de manera inversa
    print(nomTupla[-indice])

- acceder a un rango de elementos
    print(nomTupla[indiceInicial:indiceFinal])
    tener en cuenta que el indiceFinal no se imprime, se
    imprime uno atrás.

- acceder desde el índice 0 sin incluir el índice final
    print(nomTupla[:indiceFinal])

- acceder desde un índice inicial hasta el final
    print(nomTupla[indiceInicial:])

- iterar tupla:
    for elemento in nomTupla:
        # cuerpo del ciclo
        print(elemento)

- Validar si un elemento está presente
    print('elemento' in nomTupla)

* SET
    - no mantiene un orden
    - no es posible modificar elementos
    - sí es posible agregar o eliminar elementos
    - no se pueden almacenar elementos duplicados

Sintaxis:
    nomSet = {'valor', valor}

Accesibilidad:
- conocer el largo
    len(nomSet)

- Validar si un elemento está presente
    print('elemento' in nomSet)

- Agregar un nuevo elemento
    nomSet.add('valor')

- Remover un elemento 
    # posibilidad de arrojar error si no se encuentra el elemento
    nomSet.remove('elemento')

- Remover un elemento sin arrojar error
    nomSet.discard('elemento')

- Limpiar/vaciar set
    nomSet.clear()

- Eliminar completamente
    del nomSet

* DICCIONARIO
    - mutable
    - no es posible agregar claves duplicadas, si esta se
      agrega, el valor se reemplazará

Sintaxis:
    nomDiccionario = {
        clave: valor,
        clave: 'valor'
    }

Accesibilidad:
- Conocer el largo del diccionario
    len(nomDiccionario)

- Acceder a un elemento
    nomDiccionario['clave']

- Otra forma de recuperar un elemento
    nomDiccionario.get('clave')

- Modificar un elemento
    nomDiccionario['clave'] = nuevoValor

- Recorrer las claves y valores usando .items()
    for clave, valor in nomDiccionario.items():
        print(clave, ":", valor)

- Recuperar solamente las claves
    for clave in nomDiccionario.keys():
        print(clave)

- Recuperar únicamente los valores
    for valor in nomDiccionario.values():
        print(valor)

- Validar si un elemento está presente
    print('clave' in nomDiccionario)

- Agregar un elemento
    nomDiccionario['clave'] = valor

- Remover un elemento
    nomDiccionario.pop('clave')

- Limpiar/vaciar el diccionario
    nomDiccionario.clear()

- Eliminar por completo un diccionario
    del nomDiccionario
```

:pushpin: List comprehesion

Una **list comprehension** es una forma concisa y eficiente de crear listas en Python. Permite generar listas en una sola línea de código, en lugar de usar un bucle `for` tradicional.

```python
# Sintaxis:
nueva_lista = [expresión for elemento in iterable if condición]
```

> - **`expresión`** → Operación que se aplicará a cada elemento.
> - **`elemento`** → Variable que representa cada ítem en el iterable.
> - **`iterable`** → Cualquier objeto iterable (lista, rango, etc.).
> - **`if condición`** → (Opcional) Filtra elementos que cumplen la condición.

```python
# EJEMPLO FORMA TRADICIONAL
numeros = [1, 2, 3, 4, 5]
cuadrados = []  # Lista vacía

for num in numeros:
    cuadrados.append(num ** 2)  # Elevar al cuadrado y agregar a la lista

print(cuadrados)  # [1, 4, 9, 16, 25]

# EJEMPLO LIST COMPREHESION
numeros = [1, 2, 3, 4, 5]
cuadrados = [num ** 2 for num in numeros]

print(cuadrados)  # [1, 4, 9, 16, 25]
```

<img src="file:///C:/Users/Jefferson/AppData/Roaming/marktext/images/2025-02-27-09-17-22-image.png" title="" alt="" width="568">

:pushpin: Matrices

![](C:\Users\Jefferson\AppData\Roaming\marktext\images\2025-02-26-09-18-49-image.png)

:pushpin: Casting

```python
- int(nomVar) -> convierte a un entero (int)
    ej: int('10') // > 10

- float(nomVar) -> convierte a un número flotante (float)
    ej: float('10.5') // > 10.5

- str(nomVar) -> convierte a una cadena de texto (string)
    ej: str(100) // > '100'

- bool(nomVar) -> convierte a un valor booleano (True/False)
    ej: bool(0) // > False

- list() -> convierte a una lista
    ej: list((1, 2, 3)) // > [1, 2, 3]

- tuple() -> convierte a una tupla
    ej: tuple([1, 2, 3]) // > (1, 2, 3)

- set() -> convierte a un conjunto
    ej: set([1, 2, 3]) // > {1, 2, 3}

- dict() -> convierte a un diccionario
    ej: dict([(1, 'a'), (2, 'b')]) // > {1: 'a', 2: 'b'}

- complex() -> convierte a un número complejo (real + imaginario)
    ej: complex(2,3) // > (2+3j)
```

---

## TIPOS DE IMPRESION

:fire: concatenacion (+)

```python
nombre = 'jefferson'
print('hola, ' + nombre + '!')
```

:fire: (,)

Se utiliza para separar cada elemento y los imprime con espacio entre ellog.

```python
nombre = 'jefferon'
edad = 25
print("Nombre:", nombre, "Edad:", edad)
```

:fire: f-string

Los **f-strings** permiten insertar variables dentro de un texto de forma más legible.

```python
nombre = "Jefferson"
edad = 25
print(f"Me llamo {nombre} y tengo {edad} años")
```

:fire: .format()

Es otra forma de insertar variables en una cadena es `.format()`.

```python
nombre = "Jefferson"
edad = 25
print("Me llamo {} y tengo {} años".format(nombre, edad))
# {} es un marcador de posición.
# .format(nombre, edad) reemplaza {} con los valores dados.
//> Me llamo Jefferson y tengo 25 años

# renombrando los valores
print("Me llamo {nombre} y tengo {edad} años".format(nombre="Jefferson", edad=25))
```

:round_pushpin: Se pude dar formato a un numero con .format

```python
numero = 3.14159
print("{:.2f}".format(numero))
//> 3.14
# {:.2f} indica que el número tendrá 2 decimales (.2) y será float (f)

# otros formatos utiles
print(f"{numero:.1f}")   # 1 decimal → 3.1
print(f"{numero:.0f}")   # Sin decimales → 3
print(f"{numero:.4f}")   # 4 decimales → 3.1416
print(f"{numero:08.2f}") # Rellena con ceros → 00003.14
print(f"{numero:,}")     # Separador de miles → 3.142
```

:fire: end=""

Por defecto, `print()` hace un salto de línea al final. Puedes evitarlo con `end=""`.

```python
print("Hola", end=" ")
print("Mundo")
//> Hola Mundo
```

:fire: sep=""

Puedes cambiar la separación entre valores con `sep`.

```python
print("Python", "es", "genial", sep="-")
//> Python-es-genial
```

---

## OPERADORES

:fire: Aritmeticos

| Operador | Descripción                                   |
| -------- | --------------------------------------------- |
| +        | Suma                                          |
| -        | Resta                                         |
| *        | Multiplicación                                |
| /        | División                                      |
| //       | División entera (devuelve el cociente entero) |
| **       | Exponenciación                                |
| %        | Módulo (residuo de división)                  |

:fire: Asignacion

| Operador | Descripción                   |
| -------- | ----------------------------- |
| =        | Asignación de valor           |
| += n     | Suma más asignación           |
| -= n     | Resta más asignación          |
| *= n     | Multiplicación más asignación |
| /= n     | División más asignación       |
| %= n     | Módulo más asignación         |

:fire: Comparación

| Operador | Descripción          |
| -------- | -------------------- |
| ==       | Es igual que         |
| !=       | Es distinto de       |
| <        | Es menor que         |
| <=       | Es menor o igual que |
| >        | Es mayor que         |
| >=       | Es mayor o igual que |

:fire: logicos

| Operador | Descripción                                                                                             |
| -------- | ------------------------------------------------------------------------------------------------------- |
| and      | Devuelve `True` si ambas expresiones son verdaderas                                                     |
| or       | Devuelve `True` si al menos una expresión es verdadera                                                  |
| not      | Invierte el valor lógico (`True` a `False` y viceversa), operador unario, solo necesita de un operando. |

:fire: Precedencia de operadores

| Precedencia | Operador(es)                                                     | Descripción                                                   | Dirección           |
| ----------- | ---------------------------------------------------------------- | ------------------------------------------------------------- | ------------------- |
| 1 (Mayor)   | `()`                                                             | Paréntesis (agrupación)                                       | Izquierda a derecha |
| 2           | `func()`, `obj.attr`, `obj[key]`                                 | Llamadas a funciones, acceso a atributos y acceso a índices   | Izquierda a derecha |
| 3           | `**`                                                             | Potenciación (exponenciación)                                 | Derecha a izquierda |
| 4           | `+x`, `-x`, `~x`                                                 | Operadores unarios: positivo, negativo, complemento bit a bit | Derecha a izquierda |
| 5           | `*`, `/`, `//`, `%`                                              | Multiplicación, división, división entera y módulo            | Izquierda a derecha |
| 6           | `+`, `-`                                                         | Suma y resta                                                  | Izquierda a derecha |
| 7           | `<<`, `>>`                                                       | Desplazamiento de bits (izquierda, derecha)                   | Izquierda a derecha |
| 8           | `&`                                                              | AND bit a bit                                                 | Izquierda a derecha |
| 9           | `^`                                                              | XOR bit a bit                                                 | Izquierda a derecha |
| 10          | `\|`                                                             | OR bit a bit                                                  | Izquierda a derecha |
| 11          | `==`, `!=`, `>`, `<`, `>=`, `<=`, `is`, `is not`, `in`, `not in` | Comparaciones, identidad y pertenencia                        | Izquierda a derecha |
| 12          | `not`                                                            | NOT lógico                                                    | Derecha a izquierda |
| 13          | `and`                                                            | AND lógico                                                    | Izquierda a derecha |
| 14          | `or`                                                             | OR lógico                                                     | Izquierda a derecha |
| 15          | `if else`                                                        | Expresión condicional ternaria (`x if cond else y`)           | Derecha a izquierda |
| 16          | `=` y `+=`, `-=`, `*=`, `/=`, etc.                               | Asignación y operadores de asignación compuesta               | Derecha a izquierda |
| 17 (Menor)  | `,`                                                              | Separador de expresiones en tuplas, listas y funciones        | Izquierda a derecha |

---

## SENTENCIAS DE CONTROL

:fire: if-else-elif

```python
if condicion:
    # cuerpo de condicion true
elif condicion:
    # cuerpo de condicion de si no si
else:
    # cuerpo de si no
```

:fire: Operadore ternario

El **operador ternario** en Python es una forma compacta de escribir una condición `if-else` en una sola línea. Su sintaxis es:

```python
cuerpo_true if condicion else cuerpo_false
```

:fire: match-case

`match-case` es una estructura introducida en Python 3.10 que funciona de manera similar a `switch-case` en otros lenguajes. Se usa para evaluar una variable y ejecutar diferentes bloques de código según su valor.

```python
match opcion:
    # agrupacion de condiciones en un solo case
    case valor | valor | valor:
        # codigo a ejecutar
    case valor:
        # codigo a ejecutar
    case _:
        # codigo por defecto si no hay coincidencia
```

---

## BUCLES/CICLOS

:fire: while

Ciclo indeterminado.

```python
contador = 0

while condicion:
    # cuerpo del ciclo
    contador += 1
else:
 # Se ejecuta al termina el ciclo, es opcional
```

:fire: for-in

Este es un ciclo determinado, en python no se utiliza sintacis tradicional del ciclo for.

```python
for var_contenedora in secuencia:
    # codigo que se ejecuta por cada elemento de secuencia
else:
    # se ejecuta al terminar el ciclo es opcional.
```

:fire: break

Romper/terminar un ciclo.

```python
for var in secuencia:
    if condicion:
        break
else:
    # bloque que se ejecuta al finalizar.
```

:fire: continue

Omite cierta ejecucion pero continual en el ciclo.

```python
for var in secuencia:
    if condicion:
        continue # omite la ejecucion del bloque
else:
    # bloque que se ejecuta al finalizar
```

:fire: iter()

La función **`iter()`** en Python se usa para obtener un **iterador** "objeto que recuerda en qué posición del recorrido se encuentra" a partir de un objeto iterable (listas, tuplas, diccionarios, conjuntos, etc.).

```python
mi_lista = [1, 2, 3]   # Esto es un iterable
mi_iterador = iter(mi_lista)  # Convierte la lista en un iterador

print(next(mi_iterador))  # 1
print(next(mi_iterador))  # 2
print(next(mi_iterador))  # 3
```

:fire: next()

El **método `next()`** se usa para obtener el siguiente elemento de un **iterador**. Cada vez que llamamos `next()`, el iterador avanza a la siguiente posición. Si ya no hay más elementos, lanza una excepción `StopIteration`.

```python
```python
mi_lista = [1, 2, 3]   # Esto es un iterable
mi_iterador = iter(mi_lista)  # Convierte la lista en un iterador

print(next(mi_iterador))  # 1
print(next(mi_iterador))  # 2
print(next(mi_iterador))  # 3
# print(next(mi_iterador))  # ❌ StopIteration (No hay más elementos)
```

---

## FUNCIONES

```python
python
def nom_funcion(parametro = valor, parametro) -> tipoDato:
    # cuerpo funcion

nom_funcion(argumentos) # invocacion de la funcion
```

> parametro = valor -> valores por default
> 
> -> tipoDato -> hint/ tipo de dato que retorna la función

:fire: return

Cuando no se agrega un return este se agrega de forma implicita.

```python
def nombre_funcion():
    return valor # se encarga de retornar un resultado
```

:fire: *args

Argumentos variables, se suele utilizar esta forma cuando desconocemos la cantidad de argumentos que puede recibir la funcion.

```python
def nom_funcion(*args): # *variable se convierte en tupla
    print(args)
```

:fire: **kwars

Recivir elementos de clave valor

```python
def nom_funcion(**kwars): # recive un diccionario o clave='valor'
    print(kawars)

nom_funcion(clave='valor', clave=valor) # pasando clave=valor

diccionario = {
    'clave': 'vaor',
    'clave': valor
}
nom_funcion(diccionario) # pasando el diccionario
```

:fire: yield

`yield` es una palabra clave en Python que se usa dentro de una función para crear un **generador**. A diferencia de `return`, `yield` no termina la ejecución de la función, sino que **pausa** su estado y permite retomarlo más adelante.

```python
def contar_hasta(n):
    """Generador que cuenta del 1 al n."""
    for i in range(1, n + 1):
        yield i  # Pausa la función y devuelve el valor

# Crear el generador
contador = contar_hasta(5)

# Obtener valores con next()
print(next(contador))  # 1
print(next(contador))  # 2
print(next(contador))  # 3

# También se puede usar en un bucle for
for numero in contar_hasta(5):
    print(numero)  # Imprime 1, 2, 3, 4, 5


''' Explicación:
- yield, devuelve un valor y pausa la ejecución.

- La próxima vez que se llame a next(), la función 
continúa desde donde se quedó.

- Si se usa en un for, automáticamente se 
itera sobre los valores generados.
'''
```

:fire: funciones recursivas

Son funciones que se mandan a llamar asi mismas para completar cierta tarea.

:warning: **Regla importante:** Debe tener un **caso base** para evitar una recursión infinita.

```python
# Sintaxis:
def nom_funcion(param):
    # caso base (condicion de salida)
    if condicion_de_parada:
        return valorBase

    # Llamada recursiva
    return nom_funcion(nuevo_parametro)

# Ejemplo:
def factorial(n):
    # Caso base
    if n == 0:
         return 1
    else:
        # Llamada recursiva
        return n * factorial(n - 1) # el balor se pasa a la funcion

# Llamando a la función
print(factorial(5))  # Salida: 120

''' Explicación:
Caso base: Es una condición que detiene las llamadas recursivas, 
evitando que la función se llame indefinidamente.

Llamada recursiva: La función se llama a sí misma 
con nuevos parámetros, reduciendo el problema hasta llegar al caso base.

Funcionamiento:

factorial(5) llama a factorial(4),  
factorial(4) llama a factorial(3),  
Y así sucesivamente, hasta que llega a factorial(0), donde devuelve 1.

La función recursiva se va "desenrollando" y 
multiplica los resultados hasta obtener el valor final.
'''
```

:fire: Funciones lambda

Las **funciones lambda** en Python son funciones anónimas o pequeñas que se definen en una sola línea usando la palabra clave `lambda`.

Son útiles cuando necesitas una función corta y rápida sin definirla con `def`.

```python
# Sintaxis:
lambda argumentos: expresión

# Ejemplo
cuadrado = lambda x: x ** 2
print(cuadrado(4))  # Salida: 16
```

:round_pushpin: map()

La función **`map()`** se usa para aplicar una función a **cada elemento** de un iterable (como listas o tuplas) y devuelve un **iterador** con los resultados.

```python
# Sintaxis:
map(funcion, iterable)

# Ejemmplo:
numeros = [1, 2, 3, 4, 5]
dobles = list(map(lambda x: x * 2, numeros))
print(dobles)  # Salida: [2, 4, 6, 8, 10]
```

:round_pushpin: filter()

La función **`filter()`** se usa para **filtrar** elementos de un iterable **según una condición**. Solo se conservan los elementos donde la función retorna `True`.

```python
# Sintaxis:
filter(funcion, iterable)

# Ejemplo:
numeros = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
# Aquí, lambda x: x % 2 == 0 filtra solo los números pares.
pares = list(filter(lambda x: x % 2 == 0, numeros))
print(pares)  # Salida: [2, 4, 6, 8, 10]
```

---

## EXEPCIONES

El bloque `try-except` se usa para **manejar errores** y evitar que el programa se detenga cuando ocurre una excepción.

```python
try:
    # codigo que puede generar excepcion
    reusltado = 'ok'
except clase_error as nom_var_contenedora_error:
    # tratamiento del error
else:
    print("Todo salió bien:", resultado)
finally:
    print("Este bloque se ejecuta siempre.")
```

:warning: IMPORTANTE 

Si declaras una variable **dentro** del bloque `try`, pero luego intentas usarla **fuera** de este y el bloque `try` no se ejecuta completamente (por ejemplo, debido a una excepción), la variable no existirá fuera del bloque.

```python
'''
    Para evitar este problema, puedes declarar 
    la variable fuera del try con un valor por defecto:
'''
x = None  # Declarada fuera del try

try:
    x = 10 / 2  # Si no hay error, se reasigna
except ZeroDivisionError:
    print("Error: División por cero")

print(x)  # Se puede usar fuera del try
```

:pushpin: Mostrar toda la jerarquia de errores

```python
def mostrar_excepciones(base, nivel=0, prefijo="", es_ultimo=True):
    print(f"{prefijo}{'└─' if es_ultimo else '├─'} {base.__name__}")

    subclases = base.__subclasses__()
    for i, sub in enumerate(subclases):
        nuevo_prefijo = prefijo + ("   " if es_ultimo else "│  ")
        mostrar_excepciones(sub, nivel + 1, nuevo_prefijo, i == len(subclases) - 1)


mostrar_excepciones(BaseException)
```

---

## CLASES

Una clase es una plantilla que permite definir caracteristicas que tendran los objetos.

```python
class NombreClase:
    pass

'''
1. Cuando no se agrega el metodo constructor
    este se crea de manera indirecta.
2. El constructor es el metodo que permite la creacion de
    objetos.
3. Si vemos un (__) al principio de un nombre, a este se le
    conoce como meto double underscore "dunder".
'''

class NombreClase:
    ''' Constructor:
        * (self) -> es una referencia al objeto actual de la clase
        * self.nom_atributo -> indica que es un atributo de 
            instancia/objeto.
    '''
    def __init__(self, parametro):
        self.nom_atributo = parametro

    ''' Metodo:
        * Se conoce como metodo porque esta asociado a una
            clase.
        * self.nom_atributo -> de esta forma accedemos a un
            atributo de instancia.
    '''
    def nom_metodo(self, parametro):
        self.nom_atributo = parametro


    ''' Metodo GET
        * Para la creación de estos 
            requerimos de el decorador @property, que se
            utiliza en python para convertir un metodo en
            atributo de la clase.

            1. Se puede llamar sin la necesitdad de los ()
            2. Si solo creamos el metodo get sin el set
                el atributo se convertira de solo lectura
                es decir que sera inmutable.
    '''
    @property
    def nom_metodo_get(self):
        pass


    ''' Metodo SET
        * Para la creacion de estos
            requerimos un nombre y el decorador "setter"
            @nombre_atributo.setter

            1. instancia.nom_metodo_setter = valor 
    '''
    @nom_atributo.setter
    def nom_metodo_setter(self, params)
        pass


''' Instancia/objeto
    Se conoce como instancia u objeto de clase
    pues al realizar esta, este toma las propiedades
    unicamente para el objeto, es decir apuntan a
    un punto de memoria especifico.
'''
nombre_instancia = NombreClase(args)


''' Modificar valor de atributo
    Al modificar el valor, solo se esta modificando
    el valor de la instancia, es decir que solo
    altera la instancia referenciada.

    De esta forma se modifica el atributo si no tiene
    encapsulamiento.
'''
nombre_instancia.nom_atributo = valor


''' Agregar un nuevo atributo a una instancia especifica:
    Podemos agregar un nuevo atributo a una instancia
    especifica, esto quiere decir que pertenecera solo
    a esta instancia y no a las demas.
'''
nom_instancia.nom_nuevo_atributo = valor
```

:fire: IMPORTAR MODULOS/ARCHIVOS

La importacion de modulos nos permite utilizar fragmentos de codigo en archivos distintos.

```python
''' Invocar modulo en otro archivo '''
from nom_modulo import * # el (*) indica que importe todas las clases
from nom_modulo import NomClase # importa una clase en especifico

'''
    Conocer que modulo esta ciendo invocado en cierto proceso,
    esto se hace mediante el atributo especial duner __name__
    cuando este se ejecuta en la pagina activa devuelve __main__
    cuando estamos en otro modulo en donde se este invocando cierto
    metodo,clase importado se mostrara el nombre del modulo origen.
''' 
print(__name__)

''' Pruebas de codigo '''
if __name__ == '__main__':
    # Sentencias de codigo prueba
```

:fire: DESTRUCTORES

Los **destructores** son métodos especiales que se ejecutan automáticamente cuando un objeto es eliminado (desreferenciado o eliminado manualmente). En Python, el **destructor** se define con el método `__del__()`.

```python
'''
    Se invoca cuando un objeto está a punto de ser destruido o 
    recolectado por el garbage collector (recolector de basura).

    En términos simples, el metodo __del__() es el destructor de
    un objeto, y se utiliza para realizar tareas de limpieza cuando
    el objeto ya no es necesario, como liberar recursos o cerrar
    conexiones abiertas, archivos o base de datos.

    Para ello se crea un metodo dunder en la clase padre.
'''
class Persona:
    def __init__(self, nombre):
        self.nombre = nombre
        print(f"Persona {self.nombre} creada.")

    def __del__(self):
        print(f"Persona {self.nombre} eliminada.")

# Crear un objeto
p1 = Persona("Juan")

# Eliminar el objeto manualmente
del p1

# Salida esperada:
# Persona Juan creada.
# Persona Juan eliminada.
```

:fire: MRO

El método `mro()` (**Method Resolution Order**) en Python devuelve el orden en el que se buscan los métodos y atributos en una jerarquía de clases. Es útil cuando trabajas con **herencia múltiple**, ya que muestra el orden en que Python recorrerá las clases para encontrar un método o atributo

```python
class A:
    pass

class B(A):
    pass

class C(A):
    pass

# El orden en que definimos las clases extendidas es importante
class D(B, C):  # Herencia múltiple
    pass

print(D.mro())  # Muestra el orden de búsqueda

'''
    [<class '__main__.D'>, 
        <class '__main__.B'>, 
        <class '__main__.C'>, 
        <class '__main__.A'>, 
        <class 'object'>]

    Esto significa que cuando buscas un método en D, 
    Python seguirá este orden:

    1. D
    2. B
    3. C
    4. A
    5. object (clase base de todas las clases en Python)
'''
```

:fire: CLASE ABSTRACTA

Es una clase que no se puede instanciar directamente.
Es decir, no puedes crear un objeto de una clase abstracta, pero si
puede servir como base para otra clase. las clases abstractas son
útiles cuando queremos definir una estructura común que será heradada y complementada por clases derivadas.

Al crear un metodo abstracto toda la clase se transforma en abstracta, y obliga a las clases hijas a heredar metodos definidos.

```python
''' ABC
    Para crear una clase abstracta esta esta obligada a heredar de ABC 
    "Abstract Base Class". este modulo debe ser importado.

    1. se utiliza el decorador @abstractmethod para indicar que
        que el siguiente metodo sera abstracto, indicando que
        las clases hijas deben crear este metodo por obligacion.
    2. No se define cuerpo a los metodos abstractos ya que estos solo
        indican que son para su posterior implementacion.
'''
from abc import ABC, abstractmethod

class NomClase(ABC) # hereda de la clase ABC
    @abstractmethod
    def nom_metodo(self):
        pass
```

:fire: VARIABLE DE CLASE

Estas variables se asocian directamente con la clase, por lo tanto no se necesita una instancia para acceder al valor de la variable, solo necestiamos de la misma clase.

```python
class NomClase:
    # Accesible desde clase e instancia de esta
    nom_var_clase = valor

    def __init__(self, param):
        # accesible solo desde instancia
        self._varaible_instancia = param

# Acceder a la propiedad fuera de la clase
NomClase.nom_var_clase

# Definir una nueva variable de clase fuera de esta:
NomClase.nomVariable = valor
```

:fire: METODO ESTATICO DE CLASE

El decorador `@staticmethod` se usa para definir **métodos estáticos** dentro de una clase. A diferencia de los métodos de instancia (`self`) y los métodos de clase (`cls`), los métodos estáticos **no reciben ningún parámetro especial** y funcionan como funciones normales dentro de la clase.

- No reciven parametro self

- No pueden acceder a metodos/atributos de instancia o de la clase

```python
class Calculadora:
    @staticmethod
    def sumar(a, b):
        return a + b

print(Calculadora.sumar(5, 3))  # Salida: 8
```

:fire: METODO DE CLASE

El decorador `@classmethod` se usa para definir métodos de clase. A diferencia de los métodos de instancia (que reciben `self` como primer argumento), los métodos de clase reciben `cls`, que representa la propia **clase** en lugar de una instancia específica.

* No puede acceder a atributos/metodos de instancia

* Se puede acceder a atributos/metodos de clase

```python
class Ejemplo:
    atributo_clase = "Hola, soy un atributo de clase"

    @classmethod
    def mostrar(cls):
        # Accedemos a las variables de clase con cls.nom_atributo_clase
        return f"Accediendo a: {cls.atributo_clase}"

    @classmethod
    def __incrementar_contador(cls):  # Método de clase privado
        cls.__contador += 1

print(Ejemplo.mostrar())  # Se puede llamar sin crear una instancia

# Intentar acceder al método privado
print(Ejemplo.__incrementar_contador())  # AttributeError

''' Metodo de clase privado
    Si queremos un metodo de clase privado, podemos 
    combinar @classmethod con el prefijo __
'''
```

:fire: CONSTANTES DE CLASE

Por lo regular la definicion de estas constantes se crean en archivos de nombre config.py/constant.py

Aun asi, el valor de esta variable se puede modificar, es importante entender que si vemos esta convencion es indicativo de que no debemos modificar este dato.

```python
NOM_CONSTANTE = valor

--- en otro modulo ---
formo config impor NOM_CONSTANTE
```

:fire: METODOS ACCESIBLES SOLO DENTRO DE LA CLASE
En Python, un método se considera **privado** cuando su nombre comienza con **dos guiones bajos (`__`)**.

```python
class Ejemplo:
    def __init__(self, nombre):
        self.nombre = nombre  # Atributo público

    def __metodo_privado(self):
        return "Este método solo se puede usar dentro de la clase"

    def publico(self):
        return self.__metodo_privado()  # Se llama dentro de la clase

# Crear objeto
obj = Ejemplo("Python")

# Intentar acceder al método privado desde fuera
print(obj.publico())  # Se puede acceder porque es llamado dentro de la clase

print(obj.__metodo_privado())  # Error: AttributeError
```

:round_pushpin: METODOS PROTEGIDOS

Si solo quieres indicar que un método **no debería** usarse fuera de la clase (pero sigue siendo accesible), usa **un guion bajo (`_`)** al inicio.

```python
class Prueba:
    def _metodo_protegido(self):
        return "Puedo llamarse desde fuera, pero no debería"

obj = Prueba()
print(obj._metodo_protegido())  # ⚠️ Funciona, pero no es recomendado

'''
    Los métodos protegidos siguen siendo accesibles, 
    pero es una convención para que los programadores 
    sepan que no deben usarlos directamente.
'''
```

:fire: Notaciones hint

```python
class NomClase:

'''
    Puedes usar : tipo en los atributos de una clase 
    para indicar qué tipo de datos deben contener.
'''
    nom_var_clase: tipo_dato = valor


''' vehiculo: Vehiculo
    * vehiculo → Es el nombre del parámetro que recibe la función.
    * Vehiculo → Es una anotación de tipo (type hint), lo 
        que indica que el parámetro vehiculo debería ser una 
        instancia de la clase Vehiculo.

    * -> tipo_dato_retorno, indica el tipo de dato que sera
        retornado
'''
    def nom_clase(self, vehiculo: Vehiculo) -> tipo_dato_retorno
        pass
```

### HERENCIA

```python
class Padre:
    def __init__(self, parametro)
        self._parametro = parametro


''' Herencia
    Para que la herencia ocurra se debe indicar la siguiente
    sintanxis en la clase hija (ClasePadre) tambien podemos
    lograr herencia multiple (Clase1, Clase2).

    Si la clase padre posee atributos en el inicializador este
    debe inicializarse en la clase hija mediante: 
        super.__init__(parametros)
'''
class Hijo(Padre): # Herencia
    def __init__(self, parametro, parametro2):
        super().__init__(parametro) # Invocacion de clase metodo padre
        self._parametro2 = parametro2

    def nom_metodo(self):
        # llamada metodo padre
        super().nombre_metodo_padre()
```

### HERENCIA MULTIPLE

```python
'''
    Cuando la herencia es multiple, es mejor llamar a las
    clases padre dentro del inicializador de la clase hija,
    para asi diferenciar uno de otro.
'''
class NomClase(Padre1, Padre2):
    def __init__(self, parametro1, parametro2, parametro3):
        self.nom_atributo = parametro1
        # Inicializadores de clases padre
        Padre1.__init__(self, parametro2)
        Padre2.__init__(self, parametro3)

    def nom_metodo(self, param):
        '''
            Se debe pasar self explícitamente 
            porque los métodos de instancia en Python 
            esperan que el primer parámetro sea la instancia de la clase.
        '''
        Padre1.nom_metodo(self, param)
```

### SOBREESCRITURA

Basicamente son los metodos de clases padres sobreescritos en clases hija.

```python
class Padre:
    def __init__(self, param):
        self._param = param

    def __str__(self):
        return self._param

class Hija(Padre):
    def __init__(self, param1, param2):
        super().__init__(param1)
        self._param2 = param2

    # Sobreescritura del metodo padre
    def __str__(self):
        # llamando metodo de clase padre
        return f'{super().__str__()} {self._parametro2}' 
```

### POLIMORFISMO

El polimorfismo en Python (y en programación orientada a objetos en general) es un principio que permite que diferentes clases tengan métodos con el mismo nombre, pero con comportamientos diferentes según la clase que los invoque. Esto permite que una misma acción (como llamara un método) se ejecute de manera distinta dependiendo del tipo de objeto que lo invoca.

Ejemplo de polimorfismo por herencia:
Imaginemos que tienes una clase base llamada Animal, y
varias clases hijas como Perro y Gato, que sobrescriben
un método común llamado hacer_sonido.

```python
class Animal:
    def hacer_sonido(self):
        raise NotImplementedError("Este método debe ser implementado por la subclase")

class Perro(Animal):
    def hacer_sonido(self):
        return "Guau!"

class Gato(Animal):
    def hacer_sonido(self):
        return "Miau"

# Usando el polimorfismo
def hacer_sonido_del_animal(animal):
    print(animal.hacer_sonido())

# Crear instancias de las clases
perro = Perro()
gato = Gato()

# Llamamos al método de los dos animales
hacer_sonido_del_animal(perro)  # Salida: Guau!
hacer_sonido_del_animal(gato)   # Salida: Miau
```

### SOBRECARGA DE OPERADORES

La sobrecarga de operadores en Python es un concepto que permite a los programadores personalizar el comportamiento de los operadores estándar (como `+`, `-`, `*`, etc.) para objetos de clases propias.

Esto significa que puedes definir cómo deben comportarse los operadores cuando se utilizan con instancias de tus clases.

En lugar de que un operador tenga un significado fijo (por ejemplo, la suma para números), puedes definir su comportamiento para tus propias clases. Así, por ejemplo, podrías sumar dos objetos de una clase específica y determinar qué sucede en ese caso.

#### **Métodos Especiales para Sobrecarga de Operadores**

Para lograr esto, Python utiliza **métodos especiales** o **mágicos** (también llamados *dunder methods*, por sus nombres que comienzan y terminan con doble guion bajo `__`).

Algunos ejemplos comunes de estos métodos son:

- `__add__(self, other)`: Para el operador `+`.
- `__sub__(self, other)`: Para el operador `-`.
- `__mul__(self, other)`: Para el operador `*`.
- `__eq__(self, other)`: Para el operador `==`.
- `__lt__(self, other)`: Para el operador `<`.

```python
'''
    Imagina que tenemos una clase Punto que 
    representa puntos en un plano cartesiano. Queremos 
    sobrecargar el operador + para que sume las coordenadas de dos puntos.
'''
class Punto:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __add__(self, otro):
        # Sobrecargamos el operador '+' para sumar dos puntos
        if isinstance(otro, Punto):
            return Punto(self.x + otro.x, self.y + otro.y)
        return NotImplemented

    def __repr__(self):
        return f"Punto({self.x}, {self.y})"

# Crear dos puntos
p1 = Punto(1, 2)
p2 = Punto(3, 4)

# Sumar los dos puntos
p3 = p1 + p2
print(p3)  # Salida: Punto(4, 6)
```

---

## MANEJO DE ARCHIVOS

```python
'''
    este se utiliza para abrir un archivo o crear uno
    en caso de no existir, se pueden indicar parametros
    para leer informacion del archivo o para escribir
    directamente sobre este.

    rutaArchivo: debemos especificar la ubicación del archivo, 
        tener encuenta que se deben escapar 
        los "\" con "\\"" para que no lo tome como un caractere
        especial c:\\user\\desktop\\archivo.txt
        Si es mac o linux no hay necesidad 
        de escapar estos, dado a que se utiliza
el "/"

    modos:
    * 'w', especifica el modo escritura en el archivo y 
        crea el archivo si este no existe
    * 'r', especifica el modo lectura, este valor esta por default
    * 'a', append -> agregar informacion a un archivo
        sin que la anterior se elimine
    * 'x' create -> crea un arhivo especificado y 
        manda un error en caso de que ya lo este
    * 't' -> para el tipo de archivo texto, modo default
    * 'b' -> binary: modo binario (imagenes)

    Modos combinados:
    * 'w+' -> lo vamos a utilizar para escribir como leer informacion
    * 'r+' -> lo vamos a utilizar para leer informacion como para escribir

    encoding='utf8' -> set de caracteres
'''
nomVar = open('rutaArchivo', 'modo', encoding='utf8')

'''
    agregar texto aun archivo, no se permiten los acentos
    a no ser que los configuremos utf...
'''
nomVar.write('texto')

# cerrar el archivo
nomVar.close()
'''
    leer toda la informacion que contiene el archivo
    tambien podemos especificar la cantidad de caracteres
    que queremos mostrar (5)
'''
nomVar.read()

# Nos permite leer lineas de un archivo                
nomVar.readline()

# se pueden recorrer todas las lineas de un archivo con un ciclo for in
for linea in nomVarDelArchivo:
    print(linea)

'''
    esto regresa una lista, cada linea la toma como
    un dato por se parado, es decir cada linea tendria un indice
'''
nomVar.readlines()

# se puede acceder a una linea especifica dando su indice
readlines()[0]

# CREAR COPIA DEL ARCHIVO
# se crea nuevo archivo y se anexa al final del archivo
nomVarCopia = open('copia.txt', 'a') 
# se pasa lectura del archivo 1
nomVarCopia.write(nomVar.read()) 

nomVarCopia.close()
nomVar.close()
```

:fire: Otra forma de manejo de archivos

con esta forma se cierran los recursos automaticamente
with lo que hace es llamar el metodo __enter__ y al finalizar
se llama el metodo __exit__ de manera automatica

```python
with open('./ruta/archivo.txt', 'r', encoding="utf8") as nomObjeto:

print(nomObjeto.read())

# CLASE DE CONTROL PARA WITH
class ManejoArchivo:
    def __init__(self, nombreObjeto):
        self._nombreObjeto = nombreObjeto

    def __enter__(self):
        print('Obtenemos el recurso'.center(50,'-'))
        self._nombreObjeto = open('./ruta/archivo.txt', 'modo', encoding="utf8")
        return self._nomObjeto

    def __exit__(self, tipoExcepcion, valorExcepcion, trazaError):
        print('Cerramos recurso'.center(50, '-'))
        if self._nombreObjeto:
            self._nombreObjeto.close()

with ManejoArchivos('nomArchivo.txt') as nomObjeto:
    print(nomObjeto.read())
```

:fire: csv

El módulo `csv` de Python permite leer y escribir archivos en formato CSV (Comma-Separated Values). Aquí tienes una guía sobre su uso:

```python
import csv

whith open('ruta.csv', mode='r') as nombre_contenedor
    '''
        Abrir el archivo csv en modo diccionario 
        y almacenarlo en csv_lectura como un diccionario
    '''
    csv_lectura = csv.DictReader(nombre_contenedor)

    # obtener el nombre de las columnas existentes
    fieldnames = csv_lectura.fieldnames + ['total_value']


    with open('ruta.csv' mode='w', newline='') as update_file
        csv_escribir = csv.DictWriter(update_file, fieldnames=fieldnames)
        csv_escribir.writeheader() # escribir encabezados

        for row in csv_reader:
            row['total_value'] = float(row['price']) * int(row['quantity'])
            csv_escribir.writerow(row)
```

:fire: json

`json` es un módulo en Python que permite trabajar con datos en formato JSON (JavaScript Object Notation). Se usa para convertir datos de Python a JSON y viceversa.

```python
import json

# Abrir archiv json
with open('ruta.json', mode='r') as file # Abre en variable file
    # cargar json como diccionario, nom_var se convierte en diccionario
    nom_variable_diccionario = json.load(file)

# agregar informacion a un json
nom_variable_diccionario.append({'key':'value'})

with open('ruta.sjon', mode='w') as file:
    json.dump(nom_variable_diccionario, file, indent=4)
```

---

## DECORADORES:

Los **decoradores** en Python son funciones especiales que **modifican el comportamiento de otras funciones o métodos sin cambiar su código**. Se utilizan con el símbolo `@` antes del nombre del decorador.

```python
'''
    Se aplican dos decoradores en orden: 
    primero @decorador1, luego @decorador2.
    decorador1 envuelve a decorador2, que a su vez envuelve a hola().
'''


def decorador1(func):
    def nueva_funcion(*args, **kwargs):
        print("⭐ Decorador 1 antes")
        resultado = func(*args, **kwargs)
        print("⭐ Decorador 1 después")
        return resultado
    return nueva_funcion

def decorador2(func):
    def nueva_funcion(*args, **kwargs):
        print("🔹 Decorador 2 antes")
        resultado = func(*args, **kwargs)
        print("🔹 Decorador 2 después")
        return resultado
    return nueva_funcion

@decorador1
@decorador2
def hola():
    print("¡Hola, mundo!")

hola()
```

:round_pushpin: Decorador con parametros

Un **decorador con parámetros** es un decorador que acepta argumentos adicionales cuando se aplica a una función o método.

Para lograrlo, necesitamos **tres niveles de funciones anidadas**:

1. **Función externa** → Recibe los parámetros del decorador.
2. **Función intermedia** → Recibe la función que será decorada.
3. **Función interna (`wrapper`)** → Define el comportamiento antes y después de la función original.

```python
def decorador_con_parametros(prefijo):
    """Decorador que agrega un prefijo antes de ejecutar la función."""
    def decorador(func):
        def wrapper(*args, **kwargs):
            print(f"{prefijo} Ejecutando {func.__name__}...")
            resultado = func(*args, **kwargs)
            print(f"{prefijo} Finalizó {func.__name__}.")
            return resultado
        return wrapper
    return decorador  # Devolvemos el decorador personalizado

# Aplicamos el decorador con diferentes parámetros
@decorador_con_parametros("param")
def saludar(nombre):
    print(f"Hola, {nombre}!")

@decorador_con_parametros("param")
def despedirse(nombre):
    print(f"Adiós, {nombre}!")

# Llamando las funciones decoradas
saludar("Carlos")
despedirse("María")
''' Explicación
    * decorador_con_parametros(prefijo): 
        Función externa que recibe el argumento prefijo.
    * decorador(func): 
        Función intermedia que recibe la función a decorar.
    * wrapper(*args, **kwargs): 
        Función interna que ejecuta la función original, 
        agregando el prefijo.
    * Se usa @decorador_con_parametros("param") 
        para personalizar el comportamiento.
'''
```

---

## Concurrencia y paralelismo

Cuando creamos una aplicación, el manejo de tareas puede ser sencillo con pocos usuarios. Sin embargo, a medida que la aplicación gana popularidad, la gestión de un número creciente de solicitudes se complica. ¿Cómo podemos solucionar esto? A través de técnicas de **paralelismo** y **concurrencia**. Estas técnicas permiten una administración más eficiente de las tareas, especialmente en situaciones donde se requiere procesar múltiples operaciones de forma simultánea.

![](C:\Users\Jefferson\AppData\Roaming\marktext\images\2025-03-02-17-01-58-image.png)

![](C:\Users\Jefferson\AppData\Roaming\marktext\images\2025-03-02-17-28-48-image.png)

:fire: Implementacion de concurrencia

```python
'''
    En Python, la librería threading nos permite 
    introducir concurrencia a través de hilos. 
    A continuación, se muestra un ejemplo de cómo realizar esto.

    En este código, se simulan las solicitudes 
    aplicando espera de tres segundos para demostrar 
    el procesamiento concurrente.
'''
import threading
import time

def procesar_solicitud(request_id):
    print(f"Procesando solicitud {request_id}")
    time.sleep(3)
    print(f"Solicitud {request_id} completada")

hilos = []
for i in range(3):
    hilo = threading.Thread(target=procesar_solicitud, args=(i,))
    hilos.append(hilo)
    hilo.start()

for hilo in hilos:
    hilo.join()

print("Todas las solicitudes completadas")
```

:round_pushpin: Evitar Deadloock

Un **deadlock** ocurre cuando dos o más hilos se bloquean mutuamente al esperar por un recurso que está siendo utilizado por otro hilo. Para evitar esto, podemos usar `RLock` en lugar de `Lock`.

```python
'''
    Usamos RLock para evitar que múltiples operaciones 
    simultáneas en una cuenta causen bloqueos.
'''
import threading

class CuentaBancaria:
    def __init__(self, saldo):
        self.saldo = saldo
        self.lock = threading.RLock()

    def transferir(self, otra_cuenta, cantidad):
        with self.lock:
            self.saldo -= cantidad
            otra_cuenta.depositar(cantidad)

    def depositar(self, cantidad):
        with self.lock:
            self.saldo += cantidad

cuenta1 = CuentaBancaria(500)
cuenta2 = CuentaBancaria(300)

hilo1 = threading.Thread(target=cuenta1.transferir, args=(cuenta2, 200))
hilo2 = threading.Thread(target=cuenta2.transferir, args=(cuenta1, 100))

hilo1.start()
hilo2.start()

hilo1.join()
hilo2.join()

print(f"Saldo cuenta1: {cuenta1.saldo}")
print(f"Saldo cuenta2: {cuenta2.saldo}")
```

:round_pushpin: Sincronizacion de hilos

Cuando varios hilos intentan acceder a un mismo recurso al mismo tiempo, pueden ocurrir problemas de coherencia. Para evitar esto, se utilizan mecanismos de **sincronización**, como `Lock` y `RLock`, que garantizan que solo un hilo acceda a un recurso crítico a la vez.

```python
'''
    El uso de Lock asegura que solo un hilo 
    modifique la variable saldo en un momento dado, 
    evitando que el resultado final sea incorrecto.
'''
import threading

# Variable compartida
saldo = 0
lock = threading.Lock()  # Crear un Lock

def depositar(dinero):
    global saldo
    for _ in range(100000):
        with lock:  # Bloquear el acceso para evitar condiciones de carrera
            saldo += dinero

hilos = []
for _ in range(2):
    hilo = threading.Thread(target=depositar, args=(1,))
    hilos.append(hilo)
    hilo.start()

for hilo in hilos:
    hilo.join()

print(f"Saldo final: {saldo}")  # Esperamos ver 200000 como saldo
```

:fire: async

En el contexto de Python, el asincronismo se implementa mediante corrutinas—funciones que pueden detenerse y reanudarse más tarde. Esto se logra gracias a las palabras clave `async` y `await`, y la librería `asyncio` que se encarga de gestionar el "event loop", un ciclo que maneja las tareas asíncronas y devuelve las respuestas eficientemente.

Para crear funciones asíncronas en Python, es fundamental seguir ciertos pasos y utilizar las herramientas adecuadas del lenguaje. A continuación, se presenta una guía práctica para definir una función asíncrona básica:

```python
'''
    1. Importar asyncio: Esta librería es esencial 
        para ejecutar funciones asíncronas y gestionar el event loop.

    2. Definir la función con async: Utilizamos la palabra 
        reservada async para indicar que la función es asíncrona.

    3. Simular espera con await: Empleamos await junto con 
        asyncio.sleep() para simular el tiempo de espera sin 
        afectar el event loop.

    4. Retornar un resultado: Después del procesamiento,
        podemos retornar un resultado, en este caso, 
        data multiplicado por dos.

    5. Definir una función principal asíncrona: 
        Esta función, denominada main, es donde se 
        inician las corrutinas. No recibe parámetros.

    6. Ejecutar el event loop: Utilizamos asyncio.run() 
        para iniciar el loop llamando a main, nuestra función principal.
'''

import asyncio

async def process_data(data):
    print(f"procesando {data}...")
    await asyncio.sleep(10)
    print(f"{data} ya terminó de procesarse.")
    return data * 2

async def main():
    print("inicio de procesamiento")
    result = await process_data("archivo.txt")
    print(f"resultado final: {result}")

asyncio.run(main())
```

:fire: Implentacion de paralelismo

```python
'''
    Para implementar paralelismo, utilizamos multiprocessing, 
    que permite la ejecución de procesos de manera paralela. 
    Aquí tienes un ejemplo básico para calcular el cuadrado 
    de números de forma simultánea:

    El uso del pool.map en el ejemplo asegura 
    que cada número se procese en paralelo, proporcionando 
    resultados inmediatos.
'''
import multiprocessing

def calcular_cuadrado(n):
    return n * n

if __name__ == "__main__":
    numeros = [1, 2, 3, 4, 5]
    with multiprocessing.Pool() as pool:
        resultados = pool.map(calcular_cuadrado, numeros)
    print(resultados)
```

:round_pushpin: Coordinacion de tareas con multiprocessing.Manager

Cuando los procesos deben compartir estructuras de datos complejas (como listas o diccionarios), podemos usar un **Manager** para crear un espacio de memoria compartido entre procesos.

```python
'''
    multiprocessing.Manager nos permite 
    crear una lista compartida entre varios procesos, 
    facilitando la comunicación entre ellos.
'''
import multiprocessing

def agregar_valores(lista_compartida):
    for i in range(5):
        lista_compartida.append(i)

if __name__ == "__main__":
    with multiprocessing.Manager() as manager:
        lista_compartida = manager.list()

        proceso1 = multiprocessing.Process(target=agregar_valores, args=(lista_compartida,))
        proceso2 = multiprocessing.Process(target=agregar_valores, args=(lista_compartida,))

        proceso1.start()
        proceso2.start()

        proceso1.join()
        proceso2.join()

        print(f"Lista compartida: {lista_compartida}")
```

:round_pushpin: Compartir datos entre procesos multiprocessing.Queue

A diferencia de los hilos, los procesos no comparten memoria de forma predeterminada. Para que dos procesos puedan compartir datos, Python proporciona herramientas como `multiprocessing.Queue` y `multiprocessing.Value`.

```python
'''
    Usamos Queue para que el proceso secundario 
    pueda pasar datos de vuelta al proceso principal.
'''
import multiprocessing

def calcular_cuadrado(numeros, cola):
    for n in numeros:
        cola.put(n * n)

if __name__ == "__main__":
    numeros = [1, 2, 3, 4, 5]
    cola = multiprocessing.Queue()

    proceso = multiprocessing.Process(target=calcular_cuadrado, args=(numeros, cola))
    proceso.start()
    proceso.join()

    # Extraer resultados de la cola
    while not cola.empty():
        print(cola.get())
```

---

## Librerias

Libreria estandar [doc]([The Python Standard Library — Python 3.13.2 documentation](https://docs.python.org/3/library/))

Libreria externa [doc]([PyPI · El Índice de paquetes de Python](https://pypi.org/))
