## COMENTARIOS

:fire: docstring

```python
# Se colocan al inicio del archivo para describir su propósito.
""" 
Este módulo contiene funciones matemáticas básicas.
Autor: Juan Pérez
Fecha: 2025-02-26
"""

# Se colocan dentro de una funcion u/metodo
def multiplicar(a, b):
    """
    Multiplica dos números y devuelve el resultado.

    Parámetros:
    a (int, float): Primer número.
    b (int, float): Segundo número.

    Retorna:
    int, float: Resultado de la multiplicación.
    """
    return a * b


# Se colocan dentro de la clase para explicar su propósito.
class Persona:
    """Clase que representa una persona con nombre y edad."""

    def __init__(self, nombre, edad):
        """Inicializa una persona con nombre y edad."""
        self.nombre = nombre
        self.edad = edad

    def saludar(self):
        """Devuelve un saludo personalizado."""
        return f"Hola, soy {self.nombre}."

print(Persona.__doc__)  # Muestra la descripción de la clase
print(Persona.saludar.__doc__)  # Muestra la descripción del método
```

:fire: Comentario de linea

Un **comentario de línea** en Python se escribe usando el símbolo `#`, se utilizan para comentar lineas de codigo.

```python
print("Hola, mundo")  # Esto imprime un mensaje en pantalla
```
