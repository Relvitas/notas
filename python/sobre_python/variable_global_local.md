## DECLARACION DE VARIABLE

:fire: Sintaxis:

```python
identificador = 'valor'
```

**AMBITO DE VARIABLES**

Para determinar correctamente el ámbito, Python sigue la regla **LEGB**, que significa lo siguiente:

- **Ámbito local (L)**: Variables definidas en funciones o clases.

- **Ámbito envolvente (E)**: Variables definidas en funciones anidadas o de cierre.

- **Ámbito global (G)**: Variables definidas al nivel superior del módulo o archivo.

- **Ámbito incorporado (B)**: Nombres reservados en Python para funciones, módulos, palabras clave y objetos predefinidos.

:round_pushpin: **Ambito local**

Es aquella variable que se declara dentro de una funcion/clase y no puede ser usada fuera de esta dado a que genera un error.

```python
def local_function():
    x = 10 # variable local
    print(f'El valor de la variable es {x}')

print(x) # genera error dado a que es una variable local
```

:round_pushpin: **Ambito envolvente**

Significa que una función anidada dentro de otra función puede acceder a las variables de la función en la que está anidada, pero una funcion padre no puede acceder a una variable definida en una funcion hija.

```python
'''
IMPORTANTE, se pueden leer variables de la funcion externa
pero no se pueden modificar o realizar alguna accion sobre
estas, esto dado a que python entinende que son de ambito local.
'''
def funcion_externa():
    msg = 'Hola Mundo'
    def funcion_interna():
        print(msg)
    funcion_interna()

funcion_externa() # >>> Hola Mundo

# NO SE PUEDE ACCER A UNA VARIABLE HIJA DESDE PADRE

def funcion_externa():
    msg = 'Hola Mundo'
    print(res)
    def funcion_interna():
        res = 'Cruel'
        print(msg)
    funcion_interna()

funcion_externa() # >>> NameError, 'res' is not defined
```

:bulb: nonlocal

La palabra clave **`nonlocal`** se usa dentro de una función anidada para indicar que una variable pertenece a un **ámbito superior (pero no global)**.

Tienes **dos cajas** 📦:

- Caja grande → función externa

- Caja pequeña → función interna

`nonlocal` dice: “Usa la variable de la caja grande”

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

:round_pushpin: **Ambito global**

Es aquella que se declara fuera de una funcion/clase y se puede acceder a esta desde cualquier parte del programa.

```python
'''
El valor de esta se puede leer pero no modificar
'''
x = 100

def nom_funcion():
    x = 10

print(x) #100
```

:round_pushpin: global

La palabra clave **`global`** se usa dentro de una función para indicar que una variable pertenece al **ámbito global**, en lugar de ser una variable local, esto quiere decir que podemos modificar el valor de la variable global desde una funcion, tambien podemos utilizar esta palabra clave dentro de una funcion para indicar que una variable es global y asi utilizarla fuera de la funcion.

```python
contador = 0  # Variable global

def incrementar():
    global contador  # Indicamos que usaremos la variable global
    contador += 1  # Ahora sí podemos modificarla
    print(contador)

incrementar()  # Salida: 1
incrementar()  # Salida: 2

def pru_global():
    global nombre
    nombre = 'Jefferson'

print(nombre) # >>> Jefferson
```

:round_pushpin: **AMBITO INCORPORADO**

Se refiere a todas las funciones incorporadas, módulos y palabras clave de Python, y están disponibles en cualquier parte de tu programa.

```python
print(str(45)) # '45'
print(type(3.14)) # <class 'float'>
print(isinstance(3, str)) # False
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
