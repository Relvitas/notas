# **DICCIONARIOS**

Estructura de datos que almacena colecciones de pares `clave-valor`

* Con la clave se puede buscar el valor correspondiente
* Las claves deben ser únicas e inmutables
* Los valores pueden ser de cualquier tipo de dato

:bulb: Sintaxis general

```python
dictionary = {
    'key1': 'value',
    'key2': value2
}

# Ejemplo
pizza = {
    'name': 'Margherita Pizza',
    'price': 8.9,
    'calories_per_slice': 250,
    'toppings': ['mozzarella', 'basil']
}
```

:round_pushpin: **Alternativa**

Otra de las formas de crear un diccionario es mediante el constructor `dict()`, que recibe una secuencia de pares clave-valor.

:bulb: Ejemplo

```python
pizza = dict([
    ('name', 'Margherita Pizza'), 
    ('price', 8.9), 
    ('calories_per_slice', 250), 
    ('toppings', ['mozzarella', 'basil'])
])
```

**:round_pushpin:Acceder a elementos de un diccionario**

* `dictionary['clave']`
  De este modo podemos acceder a un valor, mediante su clave.
* `dictionary['clave'] = valor`
  De este modo podemos actualizar un valor.

:round_pushpin:**MÉTODOS**

* **IMPORTANTE!!**
  Un objeto vista es solo una forma de ver el contenido de un diccionario sin crear una copia separada de los datos.

* `dictionary.get(key, default)`
  Permite obtener un valor asociado a una clave y se puede establecer un valor por defecto en caso de que este no exista, de esta forma no obtendremos un error.

  ```python
  '''
  En este ejemplo se esta retornando una lista basia en caso
  de que la clave 'toppings' no tenga un valor asociado, por
  otro lado devolvera el valor correspondiente.
  '''
  pizza.get('toppings', [])
  ```

* `dictionary.keys()`
  Este método retorna un objeto vista de todas las claves del diccionario.

* `dictionary.values()`
  Este método retorna un objeto vista de todos los valores asociados a una clave. 

* `dictionary.items()`
  Este método retorna un objeto vista de todos los elementos de un diccionario.

* `dictionary.clear()`
  Este método elimina todo los elementos de un diccionario, es decir vacía la lista.

* `dictionary.pop('clave', valor_por_defecto)`
  Este método se encarga de eliminar una clave y su valor de un diccionario y retorna el valor, podemos establecer un valor por defecto en caso de que la clave no exista y retorne este.


  :bulb:Ejemplo

  ```python
  pizza = {
      'nombre': 'Margherita Pizza',
      'precio': 8.9,
      'calorias_por_rebanada': 250,
      'coberturas': ['mozzarella', 'basil']
  }
  
  print(pizza.pop('precio', 10)) # 8.9
  print(pizza.pop('precio_total')) # KeyError
  ```

* `dictionary.popitem()`
  Este método funciona a partir de la versión de Python 3.7, Con el método podemos eliminar el ultimo elemento insertado. (elimina tanto clave como valor)

* `dictionary.update('valor actualizar/nuevo')`
  Este método funcionar para actualizar un valor entorno a una clave o para agregar un nuevo par clave-valor.

  ```python
  '''
  Como podemos ver recibe la estructura de un diccionario.
  '''
  
  pizza = {
      'nombre': 'Margherita Pizza',
      'precio': 8.9,
      'calorias_por_rebanada': 250,
      'coberturas': ['mozzarella', 'basil']
  }
  
  # diccionario
  pizza.update({'precio': 15, 'tiempo_total': 25})
  # argumentos kwargs
  pizza.update(precio=15, tiempo_total=25)
  # lista de tuplas
  pizza.update([('precio', 25), ('tiempo_total', 25)])
  print(pizza.items())
  ```

