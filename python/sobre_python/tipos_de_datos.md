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

:pushpin: Matrices

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
