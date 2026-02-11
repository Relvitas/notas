**FUNCION, METODO, OPERADOR**

- **Función** → se usa con paréntesis y no pertenece a nadie

- **Método** → pertenece a un objeto (`.`)

- **Operador** → símbolo del lenguaje



**TERMINOS**

* **Subcadena** 
  Cadena de caracteres continua que forma parte de otra cadena.

* **Ocurrencia**
  Cada vez que una subcadena aparece dentro de una cadena.



**OPERADORES DE CADENA**

:round_pushpin: **<valor buscado> in <variable>**

permite consultar si una cadena contine uno o mas caracteres. esto es un operador

```python
cadena = 'Hola Mundo'
print('Hola' in cadena)
```

**FUNCIONES DE CADENA**

:round_pushpin: **len()**

permite conocer la longitud de una cadena.

```python
cadena = 'Hola'
print(len(cadena))
```

:round_pushpin: [n/-n]

los caracteres de una cadena tienen una posicion llamada indice, y para acceder a estos lo realizamos del (0 izquierda a derecha) y desde el (-1 derecha a izquierda)

```python
cadena = 'hola'
print(cadena[0])
```

* **Corte de cadena:** Es extraer una porcion de una cadena o trabajar con una parte de ella.
  
  ```python
  string[start:stop:step] 
  '''
  Tener encuenta que el ultimo caracter
  que se escribe en el stop no sera extraido
  si el 3 caracter es a este no se mostrara 
  '''
  cadena = 'Hola Mundo!'
  print(cadena[0:4])
  print(cadena[:4]) # tomara el start en 0 por defecto
  print(cadena[5:]) # tomara desde el start dado hasta el final
  '''
  El parametro step que es opcional, se utiliza para especificar
  el incremento entre cada indice en el slice
  '''
  print(cadena[0:11:2]) # Extrae cada segundo caracter
  # podemos invertir una cadena con este truco
  print(cadena[::-1])
  ```

:pushpin: **INTERPOLACION DE CADENAS**

Se conoce como interpolacion de cadenas a la accion de asignacion de variables y expresiones en una cadena.

* **f-string:** literales de cadena formateados, esta comienza por `f` seguido de las comillas simples `''` y dentro de esta se utilizan las `{}` para insertar expresiones o variables.

```python
saludo = 'Mundo'
cadena = f'hola {saludo}!'
print(cadena)
```

:pushpin: **METODOS DE CADENA/STRING**

1. `.upper()` Convierte en mayusculas el string.

2. `.lower()` Convierte una cadena de caracteres a minusculas.

3. `.strip()` Elimina los caracteres del inicio y final de una cadena.

4. `.replace('viejo', 'nuevo')` Remplazar una coincidencia por un nuevo valor en cadena.
   
   ```python
   cadena = 'Hola Mundo!'
   nueva_cadena = cadena.replace('Hola', 'hi')
   ```

5. `.split('separador')` Convierte la cadena en una lista, por medio del separador que tenga esta.
   
   ```python
   cadena = 'Hola, Mundo, desde el nuevo mundo'
   lista_cadena = cadena.split(',')
   # >>> ['Hola', 'Mundo', ' desde el nuevo mundo']
   ```

6. `'separador'.join(iterable/lista)` Concatena una lista con un separador especifico o ninguno (tener encuenta que el separado es el que se encarga de separa palabras), el metodo es del string no de la lista/iterable.
   
   ```python
   cadena = ['Hola', 'Mundo', 'Desde el nuevo mundo']
   print(' '.join(cadena))
   # >>> Hola Mundo Desde el nuevo mundo
   ```

7. `.startswith('valor_buscado')` Verifica si una cadena inicia por un valor dado, si esta inicia es true de lo contrario es false, recordar que este metodo diferencia entre mayusculas y minusculas.
   
   ```python
   cadena = 'Hola Mundo!'
   print(cadena.startswitch('H'))
   # >>> True
   print(cadena.startswtich('Hola'))
   # >>> True
   ```

8. `.endswith('valor_buscado')` Verifica si una cadena finaliza por un valor especifico.
   
   ```python
   cadena = 'Hola Mundo!'
   print(cadena.endswitch('H'))
   # >>> False
   print(cadena.endswtich('Mundo!'))
   # >>> True
   ```

9. `.find('valor_buscado')` Metodo que se encarga de buscar una subcadena en la cadena/string, este devuelve el indicie en su primera aparicion y devuelve -1 si no encuentra coincidencias.
   
   ```python
   cadena = 'Hola Mundo!'
   print(cadena.find('Mundo'))
   # >>> 5
   print(cadena.find('o'))
   # >>> 1
   print(cadena.find('1'))
   # >>> -1
   ```

10. `.count('subcadena')` Devuelve el numero de veces que una subcadena aparece en una cadena, diferencia entre mayusculas y minusculas.
    
    ```python
    cadena = 'Hola Mundo!'
    print(cadena.count('o'))
    # >>> 2
    ```

11. `.capitalize()` Devuelve una cadena con el primer caracter en mayuscula y los demas en minusculas.
    
    ```python
    cadena = 'HOLA MUNDO!'
    print(cadena.capitalize())
    # >>> Hola mundo
    ```

12. `.isupper()` Devuelve true si todos los caracteres de una cadena estan en mayuscula si no devuelve false.

13. `.islower()` Devuelve true si todos los caracteres de la cadena esta en minusculas de lo contrario devuelve false.

14. `.title()` Devuelve una cadena con la primera letra de cada palabra en mayuscula.
    
    ```python
    cadena = 'hola mundo!'
    print(cadena.title())
    # >>> Hola Mundo
    ```

15. 
