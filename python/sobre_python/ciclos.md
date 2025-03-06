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
