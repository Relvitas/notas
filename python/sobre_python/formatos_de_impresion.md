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
