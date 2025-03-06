## SENTENCIAS DE CONTROL

:fire: if-else-elif

```python
if condicion:
    # cuerpo de condicion true
elif condicion:
    # cuerpo de condicion de si no si
else:
    # cuerpo de si no
```

:fire: Operadore ternario

El **operador ternario** en Python es una forma compacta de escribir una condición `if-else` en una sola línea. Su sintaxis es:

```python
cuerpo_true if condicion else cuerpo_false
```

:fire: match-case

`match-case` es una estructura introducida en Python 3.10 que funciona de manera similar a `switch-case` en otros lenguajes. Se usa para evaluar una variable y ejecutar diferentes bloques de código según su valor.

```python
match opcion:
    # agrupacion de condiciones en un solo case
    case valor | valor | valor:
        # codigo a ejecutar
    case valor:
        # codigo a ejecutar
    case _:
        # codigo por defecto si no hay coincidencia
```
