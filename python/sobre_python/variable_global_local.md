## DECLARACION DE VARIABLE

:fire: Sintaxis:

```python
identificador = 'valor'
```

:fire: Variable tipo local

Es aquella variable que se declara dentro de una funcion y no puede ser usada fuera de esta dado a que genera un error.

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

Es aquella que se declara fuera de una funcion y se puede solo utilizar fuera de esta.

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
