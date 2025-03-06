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
