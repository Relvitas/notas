**TUPLAS (INMUTABLES)**

**IMPORTANTE!!**  NO se puede agregar, eliminar, actualizar elementos.

Una tupla es un tipo de dato de Python usado para crear una secuencia 
ordenada de valores. Las tuplas pueden contener un conjunto mixto de 
tipos de datos como este

```python
developer = ('Alice', 34, 'Rust Developer')
```

:pushpin: **ACCEDER A ELEMENTOS DE UNA TUPLA**

- Indexado positivo
  Se acceder a los elementos de izuierda a derecha, si accedermos a indices superiores a los de la lista este nos devolvera un error.
  
  ```python
  cities[0] # >>> 'Los Angeles'
  ```

- Indexado negativo
  Se accede a los elementos de derecha a izquierda
  
  ```python
  cities[-1] # >>> 'Tokyo'
  ```

:pushpin: **METODOS DE TUPLAS**

* `tupla.count(elemento)` Este metodo se encarga de contar cuantas veces aparece un elemento en una lista
  
  * Si no se pasan argumentos esta genera un TypeError.
  
  * Si no se encuentran coincidencias este retorna 0.

* `tupla.index(elemento, start, end)`
  Este metodo se encarga de retornar el indice de la primera coincidencia.
  
  * Si no encuentra ningun elemento retorna `ValueError`
  
  * Recibe 2 parametros extra start, end
    
    * `start` Desde que indice comenzar
    
    * `end` Hasta que indice sin incluir el ultimo

* `tupla.sort()` Este metodo se encarga de ordenar los elementos de una lista. al faveticamente, por numero ascendente, letras mayusculas antes. IMPORTANTE: este metodo modifica la lista directamente.
  
  ```python
  numbers = (19, 2, 35, 1, 67, 41)
  numbers.sort()
  
  print(numbers) # [1, 2, 19, 35, 41, 67]
  ```
  
  - `sorted(iterable)` Esto es una funcion que actua sobre cualquier iterable/coleccion y devuelve una lista ordenada.
  
  ```python
  numbers = [19, 2, 35, 1, 67, 41]
  sorted_numbers = sorted(numbers)
  
  print(numbers) # [19, 2, 35, 1, 67, 41]
  print(sorted_numbers) # [1, 2, 19, 35, 41, 67]
  ```
  
  - Tanto el .metodo() y la funcion() aceptan parametros opcionales `key` y `reverse`
    
    - reverse: invierte el order es decir, de menor a mayor `reverse=True` o de mayor a menor `reverse=False` este ya viene por default.
    
    - key: Especifica como comprar ej: `key=len` ordena por tamaño, entre otras llaves, consultar.

:pushpin: **FUNCIONES**

* `tuple()` Esta funcion nos permite realizar castin a un iterable y convertilo en tupla.
  
  ```python
  nombre = 'Jeffer'
  tuple(nombre)
  nombre # >>> ( 'J', 'e', 'f', 'f', 'e', 'r' )
  ```

* Acceder a una porcion de elementos de tupla
  Esto se realiza mediante el operador slice `[inicio:final:intervalo]` como en las cadenas.
  
  ```python
  """
  Recordemos que el final no se imprime, se imprime el anterior.
  """
  desserts = ('Cake', 'Cookies', 'Ice Cream', 'Pie', 'Brownies')
  print(desserts[1:4]) # >>> ('Cookies', 'Ice Cream', 'Pie')
  ```

:pushpin: **OPERADORES**

* `'string' in <iterable>` Este operador nos permite verificar si un elemento se encuetra dentro del iterable.

:pushpin: **OTROS**

* Desempaquetar elemenotos de una tupla en variables
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
  cities = [('Jefferson', 'Gonzalez', '26')
  nombre, apellido, edad = cities
  print(nombre) # >>> Jefferson
  print(apellido) # >>> Gonzalez
  print(edad) # >>> 26
  nombre2, *resto = cities
  print(nombre2) # >>> 'Jefferson'
  print(resto) # >>> ['Gonzalez', '26']
  ```
