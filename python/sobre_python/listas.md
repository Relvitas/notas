:pushpin: **LISTAS (Mutables)**

El tipo de dato lista es una secuencia ordenada de elementos que pueden 
estar compuestos por cadenas, números o incluso otras listas. Las listas
 son mutables y usan indexación basada en cero, lo que significa que el 
primer elemento de la lista está en el índice cero.

**Sintaxis**

```python
cities = ['Los Angeles', 'London', 'Tokyo']
```

Otra forma de crear una lista, es con la funcion list() que se encarga de hacer casting a un iterable (string)

```python
nombre = 'Jefferson'
lista_nombre = list(nombre)
print(lista_nombre) # >>> ['J', 'e', 'f', 'f', 'e', ...]
```

:round_pushpin:**Acceder a un elemento de la lista**

Para acceder a un elemento en la lista referenciamos este

* Indexado positivo
  Se acceder a los elementos de izuierda a derecha
  
  ```python
  cities[0] # >>> 'Los Angeles'
  ```

* Indexado negativo
  Se accede a los elementos de derecha a izquierda
  
  ```python
  cities[-1] # >>> 'Tokyo'
  ```

* Actualizar un elemto de lista
  Este se puede actualizar por medio del indice del elemento.
  
  ```python
  """
  IMPORTANTE! Si ingresamos un indice inexistente,
  python nos devolvera un error.
  """
  cities = ['Los Angeles', 'London', 'Tokyo']
  cities[0] = 'Colombia'
  print(cities) # >>> ['Colombia', 'London', 'Tokyo']
  ```

* Eliminar un elemento de la lista `del lista[indice]`
  
  ```python
  cities = ['Los Angeles', 'London', 'Tokyo']
  del cities[1]
  print(cities) # >>> ['Los Angeles', 'Tokyo']
  ```

* Verificar si un elemento se encuentra en una lista
  
  ```python
  cities = ['Los Angeles', 'London', 'Tokyo']
  print('Los Angeles' in cities) # >>> True
  print('Colombia' in cities) # >>> False
  ```

* Acceder a una lista anidada
  
  ```python
  developer = ['Alice', 25, ['Python', 'Rust', 'C++']]
  print(developer[2][1]) # >>> 'Rust'
  ```

* Desempaquetar elemenotos de una lista en variables
  Sacar los valores de una lista (o tupla) y guardarlos en variables separadas, en un solo paso. Es como abrir una caja 📦 y repartir lo que hay dentro.
  
  ```python
  """
  IMPORTANTE! se deve definir el mimo numero de variables
  que la cantidad de elemntos que contenga la lista
  de lo contrario si necesitamos recolectar cualquier 
  elemento restante de una lista utilizamos el operador 
  (*) a la ultima variable que almacenara el 
  resto de elementos en una lista. Ademos el orden en que 
  pongamos las variables es la que almacenara el elemento.
  """
  cities = ['Jefferson', 'Gonzalez', '26']
  nombre, apellido, edad = cities
  print(nombre) # >>> Jefferson
  print(apellido) # >>> Gonzalez
  print(edad) # >>> 26
  nombre2, *resto = cities
  print(nombre2) # >>> 'Jefferson'
  print(resto) # >>> ['Gonzalez', '26']
  ```

* Acceder a una porcion de elementos de lista
  Esto se realiza mediante el operador slice `inicio:final:intervalo` como en las cadenas
  
  ```python
  """
  Recordemos que el final no se imprime, se imprime el anterior.
  """
  desserts = ['Cake', 'Cookies', 'Ice Cream', 'Pie', 'Brownies']
  print(desserts[1:4]) # >>> ['Cookies', 'Ice Cream', 'Pie']
  ```

:round_pushpin:**METODOS DE LISTA**

* `lista.append(valor)` Este metodo se utiliza para agregar un elemento al final de la lista, de igual forma este metodo funciona para agregar otra lista dentro de la lista al final.
  
  ```python
  numbers = [1, 2, 3, 4, 5]
  even_numbers = [6, 8, 10]
  
  numbers.append(even_numbers)
  print(numbers) # [1, 2, 3, 4, 5, [6, 8, 10]]
  ```
  
  * `lista.extend(lista)` Este metodo se encarga de agregar cada elemento de una lista individualmente a otra lista
  
  ```python
  numbers = [1, 2, 3, 4, 5]
  even_numbers = [6, 8, 10]
  
  numbers.extend(even_numbers)
  print(numbers) # [1, 2, 3, 4, 5, 6, 8, 10]
  ```

* `lista.isert(elemento)` Este metodo se encarga de insertar un elemento en un indice especificado por nosotros, recibe indice y elemento.
  
  ```python
  numbers = [1, 2, 3, 4, 5]
  numbers.insert(2, 2.5)
  print(numbers) # >>> [1, 2, 2.5, 3, 4, 5]
  ```

* `lista.remove(elemento)` Este metodo se encarga de eliminar un elemento de una lista dando un valor que se encuentre dentro de la lista, si esta contiene mas de un elemento solo elimina la primera ocurrencia las demas las deja intactas.
  
  ```python
  numbers = [10, 20, 30, 40, 50, 50, 50]
  numbers.remove(50)
  
  print(numbers) # [10, 20, 30, 40, 50, 50]
  ```

* `lista.pop(elemento)` Eliminar un elemento de una lista especifico, dado su indice.
  
  IMPORTANTE: Si no especificamos un elemento, se eliminara el ultimo de la lista.
  
  ```python
  guitarras = ['Yamaha', 'Gibson', 'Vorson', 'Italica']
  guitarras.pop(3) # >>> ['Yamaha', 'Gibson', 'Vorson' ]
  guitarras.pop() # >>> ['Yamaha', 'Gibson' ]
  ```

* `lista.clear()` Este metodo elimina todos los elementos de una lista, dejando esta vacia.

* `lista.sort()` Este metodo se encarga de ordenar los elementos de una lista. al faveticamente, por numero ascendente, letras mayusculas antes. IMPORTANTE: este metodo modifica la lista directamente.
  
  ```python
  numbers = [19, 2, 35, 1, 67, 41]
  numbers.sort()
  
  print(numbers) # [1, 2, 19, 35, 41, 67]
  ```
  
  * `sorted(iterable)` Esto es una funcion que actua sobre cualquier iterable/coleccion y devuelve una lista ordenada.
  
  ```python
  numbers = [19, 2, 35, 1, 67, 41]
  sorted_numbers = sorted(numbers)
  
  print(numbers) # [19, 2, 35, 1, 67, 41]
  print(sorted_numbers) # [1, 2, 19, 35, 41, 67]
  ```
  
  * Tanto el .metodo() y la funcion() aceptan parametros opcionales `key` y `reverse`
    
    * reverse: invierte el order es decir, de menor a mayor `reverse=True` o de mayor a menor `reverse=False` este ya viene por default.
    
    * key: Especifica como comprar ej: `key=len` ordena por tamaño, entre otras llaves, consultar.

* `lista.reverse()` Este metodo se encarga de invertir una lista de elementos.
  
  ```python
  numbers = [6, 5, 4, 3, 2, 1]
  numbers.reverse()
  
  print(numbers) # [1, 2, 3, 4, 5, 6]
  ```

* `lista.index(valor, inicio, fin)` Este metodo se encarga de buscar el primer elemento en una lista de elementos y devuelve su indice, de no encontrase una coincidencia devuelve `ValueError` .
  
  ```python
  guitarras = ['Gibson', 'Yamana', 'Vorson', 'Gibson']
  print(guitarras.index('Gibson')) # >>> 0
  ```

  * valor: elemento a buscar
  * inicio (opcional): desde que posición buscar
  * fin (opcional): hasta que posición buscar
  

:pushpin: **FUNCIONES**

* `len(lista)`
  Devuelve el numero total de elemtos de una lista

* `filter()`
  Es una función que **filtra** elementos de una lista (o cualquier iterable) según una condición. Es como un colador que solo deja pasar lo que cumple cierta regla. Devuelve un objeto especial, así que normalmente lo conviertes a lista con `list()`
  
  ```python
  # Sintaxis
  filter(función_condición, iterable)
  ```
  
  * **función_condición**: una función que retorna `True` o `False`
  
  * **iterable**: la lista, tupla, etc. que quieres filtrar

* :bulb: Ejemplo
  
  ```python
  numeros = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
  
  def es_par(x):
      return x % 2 == 0
  
  resultado = filter(es_par, numeros)
  print(list(resultado))
  # [2, 4, 6, 8, 10]
  ```

* `map()`
  Es una función que **transforma** cada elemento de una lista (o iterable) aplicándole una función. Es como una fábrica que procesa cada elemento y te devuelve el resultado. Devuelve un objeto especial, así que normalmente lo conviertes a lista con `list()`.
  
  ```python
  # Sintaxis
  map(función_transformación, iterable)
  ```
  
  - **función_transformación**: la función que se aplica a cada elemento
  - **iterable**: la lista, tupla, etc. que quieres transformar

* :bulb: Ejemplo
  
  ```python
  numeros = [1, 2, 3, 4, 5]
  
  def duplicar(x):
      return x * 2
  
  resultado = map(duplicar, numeros)
  print(list(resultado))
  # [2, 4, 6, 8, 10]
  ```

* `sum()`
  Es una función que **suma todos los elementos** de una lista (o iterable) y devuelve el total.
  
  ```python
  # Sintaxis
  sum(iterable, start=0)
  ```
  
  * **iterable** (obligatorio): La lista, tupla, etc. que quieres sumar
  - **start** (opcional): Un valor inicial desde donde empieza la suma (por defecto es 0

* :bulb: Ejemplo
  
  ```python
  numeros = [1, 2, 3, 4, 5]
  
  # Sin start (por defecto es 0)
  total1 = sum(numeros)
  print(total1)  # 15
  
  # Con start = 10
  # se puede indicar start=10 o solo 10
  total2 = sum(numeros, 10)
  print(total2)  # 25
  ```
  

* `zip()`
  Permite combinar dos o más iterables (listas, tuplas, etc.) elemento por elemento, creando tuplas con los elementos correspondientes de cada iterable.

* :bulb: Ejemplo

  ```python
  '''
  Toma elementos de la misma posición de cada iterable y los agrupa en tuplas. Se detiene cuando el iterable más corto se agota.
  '''
  nombres = ['Ana', 'Luis', 'Carlos']
  edades = [25, 30, 22]
  
  for nombre, edad in zip(nombres, edades):
      print(f"{nombre} tiene {edad} años")
  
  # Salida:
  # Ana tiene 25 años
  # Luis tiene 30 años
  # Carlos tiene 22 años
  ```

   

:pushpin: **OPERADORES**

* `del lista[index]` Elimina el elemento de la lista. 



:pushpin:**LIST COMPREHENSION**

(compresion de lista) es una forma concisa y elegante de crear listas en Python. Te permite generar una nueva lista aplicando una expresión a cada elemento de un iterable, todo en una sola línea.

```python
NOMBRE_LISTA = [QUÉ_PONER for ELEMENTO in LISTA if CONDICIÓN]
```

- **QUÉ_PONER**: lo que quieres guardar
- **ELEMENTO**: cada cosa de tu lista
- **LISTA**: de dónde sacas las cosas
- **if CONDICIÓN**: (opcional) solo si cumple algo

**IMPORTANTE**

La ubicacion del if/else

- **Izquierda (if-else)** = Transforma pero **mantiene todos** los elementos
- **Derecha (solo if)** = Filtra y **elimina** algunos elementos

:bulb: Ejemplos:

```python
even_numbers = [num for num in range(21) if num % 2 == 0]
print(even_numbers)

numeros = [1, 2, 3, 4, 5]

etiquetas = ['par' if n % 2 == 0 else 'impar' for n in numeros]
print(etiquetas)  # ['impar', 'par', 'impar', 'par', 'impar']
```
