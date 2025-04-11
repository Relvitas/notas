## Metodos de cadenas

1. `str.capitalize()`
   
   Este metodo convierte solo la primera letra de un string en mayuscula y el resto de la cadena se convierte a minuscula.
   
   ```python
   print('hola MuNdo'.capitalize())
   
   > Hola mundo 
   ```

2. `str.casefold()`
   
   Este metodo se encarga de normalizar/convertir a minusculas una cadena, es un metodo mas agresivo que lower() pues este convierte si o si a minusculas.
   
   ```python
   print('Hola MuNdo'.casefold())
   
   > hola mundo
   ```

3. `str.center(width, 'caracter')`
   
   Este se encarga de centrar una cadena en base a un ancho definido en (width), podemos pasar cualquier carcater que se utilizar como relleno. si pasamos un ancho de 25 y la cadena tiene 10, esta ocupara entonces 15 caracteres mas, dado a que los caracteres del string tambien cuentan.
   
   ```python
   print(' Hola Mundo '.center(25, '-'))
   
   > ------- Hola Mundo ------
   ```

4. `str.count(subcadena, inicio, fin)`
   
   Este metodo nos sirve para contar la cantidad de apariciones de una subcadena en una cadena inicial.
   
   inicio -> opcional
   
   fin -> opcional
   
   ```python
   print('Hola Mundo'.conunt('o'))
   
   # imprime 2 dado a que esa es la cantidad de veces que aparece
   > 2
   ```

5. `str.endswith(texto/tupla, desde, hasta)`
   
   Este metodo nos permite realizar una busqueda al final de una cadena, tambien permite pasar una tapla, tener encuenta que este metodo es case sensitive
   
   ```python
   texto = 'Hola Mundo.txt'
   print(texto.endswith('.txt'))
   
   # Si el valor coicide devuelve True de lo contrario False
   > True
   ```

6. `str.expandtabs(n)`
   
   Este metodo permite decidir cuantos espacios queremos asignar a los tab de un string, por defecto son 8 tabs, pero podemos cambiar este.
   
   ```python
   texto = 'Hola\tMundo'
   
   print(texto.expandtabs(4))
   
   # Imprime cuatro espacios en vez de 8
   > Hola    Mundo
   ```

7. `str.find(texto, desde, hasta)`
   
   Busca un texto dentro de otro texto y te dice en qué posición empieza la palabra que encontró, este metodo retorna -1 si no encuentra coincidencias.
   
   Este metodo es funcional si queremos conocer la posicion de cierta subcadena, de lo contrario si solo queremos saber si esta presente podemos utilizar el metodo in.
   
   ```python
   texto = 'Hola Mundo'
   print(texto.find('undo'))
   
   # Nos dira la ubicacion desde la primera palabra de la subcadena
   > 6
   
   # CONOCER SI ESTA EN LA CADENA
   'Hola' in texto
   
   # Este retorna True o False si existe o no
   > True
   ```
   
   :round_pushpin: `str.index(texto, desde, hasta)`
   
   Funciona de la misma forma que `find()` con la unica diferencia de que si no encuentra coincidencias este lanzara una exepcion de tipo `ValueError`.
   
   ```python
   texto = 'Hola Mundo'
   print(texto.index('undo'))
   
   # Nos dira la ubicacion desde la primera palabra de la subcadena
   > 6
   ```

8. `str.format(*args, **kwargs)`
   
   Te ayuda a poner variables dentro de un texto fácilmente. con ayuda de `{}` dentro del string.
   
   se puede pasar una lista, que asigna valores por posicion o pasar un diccionario que asigna los valores por key.
   
   ```python
   texto = 'Hola {} desde {}'
   print(texto.format('Mundo', 'Casa'))
   
   # Agrega los valores segun la posicion de asignacion
   > Hola Mundo
   
   # Importante tener encuenta que si pasamos una lista debemos
   # desempaquetar esta con * para que el codigo los interprete
   # como argumentos posicionales por separado, de lo contrario
   # ubicar los elementos de la lista por posicion en format
   # ejemplo format('Mundo', 'Casa')
   texto = 'Hola {} desde {}'
   contenido = ['Mundo', 'Casa']
   print(texto.format(*contenido))
   
   # Otra forma es pasa clave=valor, insertando la posicion en el string
   # Importante tener encuenta que si pasamos un diccionario
   # debemos utilizar ** que desempaquetan este para que el codigo
   # entienda que es lo que queremos hacer. O podemos asignar
   # la clave valor directamente 
   # format(posicion1='Hola', posicion2='Casa')
   texto = 'Hola {posicion1} desde {posicion2}'
   contenido = {
       'posicion1': 'Mundo',
       'posicion2': 'Casa'
   }
   print(texto.format(**contenido))
   ```

9. `str.isalnum()`
   
   Este metodo nos ayuda a validar si todos los caracteres del string son alfa numericos, es decir que si hay simbolos, espacios este nos dira False. debe contener al menos un caracter o tambien dira False.
   
   ```python
   texto = 'Hola Mundo'
   print(texto.isalnum())
   
   # Retorna false dado a que hay un espacio.
   > False
   ```

10. `str.isalpha()`
    
    Este metodo nos sirve para validar si el string contiene solo letras, de lo contrario dira False, es decir que este no puede contener numero ni signos.
    
    ```python
    texto = 'Hola'
    print(texto.isalpha())
    
    # Es true dado a que solo hay letras
    > True
    ```

11. `str.isascii()`
    
    Este metodo no sirve para validar si los caracteres que contiene el string con carcateres ascii si es asi este devolvera True de lo contrario False, tener encuenta que la ñ no cuenta como ascii.
    
    ```python
    texto = 'niño'
    print(texto.isascii())
    
    # Imprimira false dado a que la ñ no es un carater ascii
    > False
    ```

12. `str.isdecimal()`
    
    Este metodo valida si los numeros que contiene el string son decimales, es decir numeros del `0-9` pero este no valida los numeros despues de un punto o una coma, devolvera false de ser asi.
    
    ```python
    decimal = '123.3'
    print(decimal.isdecimal())
    
    # Devuelve false dado a que hay presente un punto
    > False
    ```
    
    :round_pushpin: `str.isdigit()`
    
    Es un metodo como `isdecimal()` con la unica diferencia de que admite numero elevados o fracciones.
    
    ```python
    digitos = '12²'
    print(digitos.isdigit())
    
    # Imprime True dado a que es valido
    > True
    ```

13. `str.isidentifier()`
    
    Este metodo permite validar si un string puede ser utilizado como nombre en python. veamos esto como los identificadores en variables, claves de diccionario, funciones etc.
    
    ```python
    texto = '2mundo'
    print(texto.isidentifies())
    
    # Imprimira False dado a que no puede comenzar con numero
    > False
    ```

14. `str.islower()`
    
    Este metodo valida si todos los caracteres del string estan en minuscula de lo contrario mostrara False.
    
    ```python
    texto = 'Mundo'
    print(texto.islower())
    
    # Retorna False dado a que la M no es minuscula
    > False
    ```
