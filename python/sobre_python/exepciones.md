## EXEPCIONES

El bloque `try-except` se usa para **manejar errores** y evitar que el programa se detenga cuando ocurre una excepción.

```python
try:
    # codigo que puede generar excepcion
    reusltado = 'ok'
except clase_error as nom_var_contenedora_error:
    # tratamiento del error
else:
    print("Todo salió bien:", resultado)
finally:
    print("Este bloque se ejecuta siempre.")
```

:warning: IMPORTANTE

Si declaras una variable **dentro** del bloque `try`, pero luego intentas usarla **fuera** de este y el bloque `try` no se ejecuta completamente (por ejemplo, debido a una excepción), la variable no existirá fuera del bloque.

```python
'''
    Para evitar este problema, puedes declarar 
    la variable fuera del try con un valor por defecto:
'''
x = None  # Declarada fuera del try

try:
    x = 10 / 2  # Si no hay error, se reasigna
except ZeroDivisionError:
    print("Error: División por cero")

print(x)  # Se puede usar fuera del try
```

:pushpin: Mostrar toda la jerarquia de errores

```python
def mostrar_excepciones(base, nivel=0, prefijo="", es_ultimo=True):
    print(f"{prefijo}{'└─' if es_ultimo else '├─'} {base.__name__}")

    subclases = base.__subclasses__()
    for i, sub in enumerate(subclases):
        nuevo_prefijo = prefijo + ("   " if es_ultimo else "│  ")
        mostrar_excepciones(sub, nivel + 1, nuevo_prefijo, i == len(subclases) - 1)


mostrar_excepciones(BaseException)
```
