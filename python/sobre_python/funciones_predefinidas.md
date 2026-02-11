**FUNCIONES PREDEFINIDAS**

* **CASTING**
  Se le conoce como la conversion de tipos
  
  * `int()` Convertir a entero
  
  * `float()` Convertir a punto/coma flotante
  
  * `str()` Convertir a string
  
  * `bool()` Convierte un valor a booleano, de esta forma sabremos si un dato es de tipo `True` o `False`

* `round(objeto, ndcimales)` redondea un numero a unumero especifico de lugar de decimales. Por defecto, esta funcion redondea al entero mas cercano y devuelve un numero entero sin decimales.
  
  ```python
  num = 1.6
  print(round(num))
  # >>> 2
  #! IMPORTANTE el redonde aplica apartir del 6
  ```

* `abs()` Devuelve el valor absoluto de un numero, es decir sin el signo.
  
  ```python
  num = -8
  print(abs(num))
  # >>> 8
  ```

* `pow(base, exponente, opc-modulo)` Elevar un numero a una potencia
  
  ```python
  # (base ** exponente) % modulo
  print(pow(2, 3, 5)) # (2 ** 3) % 5
  # >>> 3
  ```

* `maketrans()` Crea una tabla de traduccion, es como un diccionario especial que dice, esta letra se cambia por esta letra.
  
  ```python
  '''
  toma dos cadenas de igual longitud y devuelve 
  una tabla de traducción que asigna cada carácter 
  de la primera cadena con el carácter correspondiente 
  de la segunda cadena
  '''
  tabla = str.maketrans("aeiou", "12345")
  ''' Esto es lo que esta sucediendo
  a → 1
  e → 2
  i → 3
  o → 4
  u → 5
  '''
  ```
  
  * se utiliza en conjunto con `translate()` **aplica una tabla de traducción a una cadena de texto**, reemplazando o eliminando caracteres según las reglas definidas.
  
    - `maketrans()` 👉 **define las reglas**
  
    - `translate()` 👉 **ejecuta las reglas**

```python
texto = "hola mundo"
print(texto.translate(tabla))
# >>> h4l1 m5nd4
```

* `range()` Esta funcion se utiliza para generar una secuencia de enteros.
  
  ```python
  """
  start: por defecto viene en 0 que indica desde donde
  queremos comenzar la secuencia de numeros.
  stop: indica hasta donde generar numeros, esto sin
  incluir el numero final, es decir si es 5 solo iria
  hasta el .
  step: indica de cuanto en cuanto realizar el 
  incremento a la secuencia.
  """
  range(start, stop, step)
  
  for num in range(2, 11, 2):
      print(num)
  
  # >>> 2, 4, 6, 8, 10
  ```
  
  * Si no se proprocionan argumentos esta devolvera un TypeError.
  * Esta funcion solo recibe enteros, si asignamos flotantes esta nos devolvera un `TypeError`
  * Tambien se puede lograr una secuencia decreciente, con el step en negativo y un start en positivo.

* `enumerate(iterable, start=n)` Esta funcion se encarga de llevar un contador ya sea de una (lista, tupla, string) generando un objeto que contiene tuplas.

```python
 """
iterable: acemos referencia a la coleccion de datos
lista, tupla, string.
start=n: Indicamos en que numero debe empezar el
contador.
"""
enumerate(iterable, start=0)

frutas = ['manzana', 'banana', 'naranja']

for indice, fruta in enumerate(frutas):
    print(f"{indice}: {fruta}")

# Salida:
# 0: manzana
# 1: banana
# 2: naranja
```

* `zip()` Permite combinar dos o más iterables (listas, tuplas, etc.) elemento por elemento, creando tuplas con los elementos correspondientes de cada iterable.
  
  ```python
  zip(iterable1, iterable2, ...)
  ```
  
  * `zip()` toma elementos de la misma posición de cada iterable y los agrupa en tuplas. Se detiene cuando el iterable más corto se agota.
  
  ```python
  nombres = ['Ana', 'Luis', 'Carlos']
  edades = [25, 30, 22]
  
  for nombre, edad in zip(nombres, edades):
      print(f"{nombre} tiene {edad} años")
  
  # Salida:
  # Ana tiene 25 años
  # Luis tiene 30 años
  # Carlos tiene 22 años
  ```

* 
