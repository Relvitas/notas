## DECORADORES:

Los **decoradores** en Python son funciones especiales que **modifican el comportamiento de otras funciones o métodos sin cambiar su código**. Se utilizan con el símbolo `@` antes del nombre del decorador.

```python
'''
    Se aplican dos decoradores en orden: 
    primero @decorador1, luego @decorador2.
    decorador1 envuelve a decorador2, que a su vez envuelve a hola().
'''


def decorador1(func):
    def nueva_funcion(*args, **kwargs):
        print("⭐ Decorador 1 antes")
        resultado = func(*args, **kwargs)
        print("⭐ Decorador 1 después")
        return resultado
    return nueva_funcion

def decorador2(func):
    def nueva_funcion(*args, **kwargs):
        print("🔹 Decorador 2 antes")
        resultado = func(*args, **kwargs)
        print("🔹 Decorador 2 después")
        return resultado
    return nueva_funcion

@decorador1
@decorador2
def hola():
    print("¡Hola, mundo!")

hola()
```

:round_pushpin: Decorador con parametros

Un **decorador con parámetros** es un decorador que acepta argumentos adicionales cuando se aplica a una función o método.

Para lograrlo, necesitamos **tres niveles de funciones anidadas**:

1. **Función externa** → Recibe los parámetros del decorador.
2. **Función intermedia** → Recibe la función que será decorada.
3. **Función interna (`wrapper`)** → Define el comportamiento antes y después de la función original.

```python
def decorador_con_parametros(prefijo):
    """Decorador que agrega un prefijo antes de ejecutar la función."""
    def decorador(func):
        def wrapper(*args, **kwargs):
            print(f"{prefijo} Ejecutando {func.__name__}...")
            resultado = func(*args, **kwargs)
            print(f"{prefijo} Finalizó {func.__name__}.")
            return resultado
        return wrapper
    return decorador  # Devolvemos el decorador personalizado

# Aplicamos el decorador con diferentes parámetros
@decorador_con_parametros("param")
def saludar(nombre):
    print(f"Hola, {nombre}!")

@decorador_con_parametros("param")
def despedirse(nombre):
    print(f"Adiós, {nombre}!")

# Llamando las funciones decoradas
saludar("Carlos")
despedirse("María")
''' Explicación
    * decorador_con_parametros(prefijo): 
        Función externa que recibe el argumento prefijo.
    * decorador(func): 
        Función intermedia que recibe la función a decorar.
    * wrapper(*args, **kwargs): 
        Función interna que ejecuta la función original, 
        agregando el prefijo.
    * Se usa @decorador_con_parametros("param") 
        para personalizar el comportamiento.
'''
```
