## OPERADORES

:fire: Aritmeticos

| Operador | Descripción                                   |
| -------- | --------------------------------------------- |
| +        | Suma                                          |
| -        | Resta                                         |
| *        | Multiplicación                                |
| /        | División                                      |
| //       | División entera (devuelve el cociente entero) |
| **       | Exponenciación                                |
| %        | Módulo (residuo de división)                  |

:fire: Asignacion

| Operador | Descripción                   |
| -------- | ----------------------------- |
| =        | Asignación de valor           |
| += n     | Suma más asignación           |
| -= n     | Resta más asignación          |
| *= n     | Multiplicación más asignación |
| /= n     | División más asignación       |
| %= n     | Módulo más asignación         |

:fire: Comparación

| Operador | Descripción          |
| -------- | -------------------- |
| ==       | Es igual que         |
| !=       | Es distinto de       |
| <        | Es menor que         |
| <=       | Es menor o igual que |
| >        | Es mayor que         |
| >=       | Es mayor o igual que |

:fire: logicos

| Operador | Descripción                                                                                             |
| -------- | ------------------------------------------------------------------------------------------------------- |
| and      | Devuelve `True` si ambas expresiones son verdaderas                                                     |
| or       | Devuelve `True` si al menos una expresión es verdadera                                                  |
| not      | Invierte el valor lógico (`True` a `False` y viceversa), operador unario, solo necesita de un operando. |

---

## Precedencia de operadores

| Precedencia | Operador(es)                                                     | Descripción                                                   | Dirección           |
| ----------- | ---------------------------------------------------------------- | ------------------------------------------------------------- | ------------------- |
| 1 (Mayor)   | `()`                                                             | Paréntesis (agrupación)                                       | Izquierda a derecha |
| 2           | `func()`, `obj.attr`, `obj[key]`                                 | Llamadas a funciones, acceso a atributos y acceso a índices   | Izquierda a derecha |
| 3           | `**`                                                             | Potenciación (exponenciación)                                 | Derecha a izquierda |
| 4           | `+x`, `-x`, `~x`                                                 | Operadores unarios: positivo, negativo, complemento bit a bit | Derecha a izquierda |
| 5           | `*`, `/`, `//`, `%`                                              | Multiplicación, división, división entera y módulo            | Izquierda a derecha |
| 6           | `+`, `-`                                                         | Suma y resta                                                  | Izquierda a derecha |
| 7           | `<<`, `>>`                                                       | Desplazamiento de bits (izquierda, derecha)                   | Izquierda a derecha |
| 8           | `&`                                                              | AND bit a bit                                                 | Izquierda a derecha |
| 9           | `^`                                                              | XOR bit a bit                                                 | Izquierda a derecha |
| 10          | `\|`                                                             | OR bit a bit                                                  | Izquierda a derecha |
| 11          | `==`, `!=`, `>`, `<`, `>=`, `<=`, `is`, `is not`, `in`, `not in` | Comparaciones, identidad y pertenencia                        | Izquierda a derecha |
| 12          | `not`                                                            | NOT lógico                                                    | Derecha a izquierda |
| 13          | `and`                                                            | AND lógico                                                    | Izquierda a derecha |
| 14          | `or`                                                             | OR lógico                                                     | Izquierda a derecha |
| 15          | `if else`                                                        | Expresión condicional ternaria (`x if cond else y`)           | Derecha a izquierda |
| 16          | `=` y `+=`, `-=`, `*=`, `/=`, etc.                               | Asignación y operadores de asignación compuesta               | Derecha a izquierda |
| 17 (Menor)  | `,`                                                              | Separador de expresiones en tuplas, listas y funciones        | Izquierda a derecha |
