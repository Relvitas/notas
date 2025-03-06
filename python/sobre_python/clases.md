## CLASES

Una clase es una plantilla que permite definir caracteristicas que tendran los objetos.

```python
class NombreClase:
    pass

'''
1. Cuando no se agrega el metodo constructor
    este se crea de manera indirecta.
2. El constructor es el metodo que permite la creacion de
    objetos.
3. Si vemos un (__) al principio de un nombre, a este se le
    conoce como meto double underscore "dunder".
'''

class NombreClase:
    ''' Constructor:
        * (self) -> es una referencia al objeto actual de la clase
        * self.nom_atributo -> indica que es un atributo de 
            instancia/objeto.
    '''
    def __init__(self, parametro):
        self.nom_atributo = parametro

    ''' Metodo:
        * Se conoce como metodo porque esta asociado a una
            clase.
        * self.nom_atributo -> de esta forma accedemos a un
            atributo de instancia.
    '''
    def nom_metodo(self, parametro):
        self.nom_atributo = parametro


    ''' Metodo GET
        * Para la creación de estos 
            requerimos de el decorador @property, que se
            utiliza en python para convertir un metodo en
            atributo de la clase.

            1. Se puede llamar sin la necesitdad de los ()
            2. Si solo creamos el metodo get sin el set
                el atributo se convertira de solo lectura
                es decir que sera inmutable.
    '''
    @property
    def nom_metodo_get(self):
        pass


    ''' Metodo SET
        * Para la creacion de estos
            requerimos un nombre y el decorador "setter"
            @nombre_atributo.setter

            1. instancia.nom_metodo_setter = valor 
    '''
    @nom_atributo.setter
    def nom_metodo_setter(self, params)
        pass


''' Instancia/objeto
    Se conoce como instancia u objeto de clase
    pues al realizar esta, este toma las propiedades
    unicamente para el objeto, es decir apuntan a
    un punto de memoria especifico.
'''
nombre_instancia = NombreClase(args)


''' Modificar valor de atributo
    Al modificar el valor, solo se esta modificando
    el valor de la instancia, es decir que solo
    altera la instancia referenciada.

    De esta forma se modifica el atributo si no tiene
    encapsulamiento.
'''
nombre_instancia.nom_atributo = valor


''' Agregar un nuevo atributo a una instancia especifica:
    Podemos agregar un nuevo atributo a una instancia
    especifica, esto quiere decir que pertenecera solo
    a esta instancia y no a las demas.
'''
nom_instancia.nom_nuevo_atributo = valor
```

:fire: IMPORTAR MODULOS/ARCHIVOS

La importacion de modulos nos permite utilizar fragmentos de codigo en archivos distintos.

```python
''' Invocar modulo en otro archivo '''
from nom_modulo import * # el (*) indica que importe todas las clases
from nom_modulo import NomClase # importa una clase en especifico

'''
    Conocer que modulo esta ciendo invocado en cierto proceso,
    esto se hace mediante el atributo especial duner __name__
    cuando este se ejecuta en la pagina activa devuelve __main__
    cuando estamos en otro modulo en donde se este invocando cierto
    metodo,clase importado se mostrara el nombre del modulo origen.
''' 
print(__name__)

''' Pruebas de codigo '''
if __name__ == '__main__':
    # Sentencias de codigo prueba
```

:fire: DESTRUCTORES

Los **destructores** son métodos especiales que se ejecutan automáticamente cuando un objeto es eliminado (desreferenciado o eliminado manualmente). En Python, el **destructor** se define con el método `__del__()`.

```python
'''
    Se invoca cuando un objeto está a punto de ser destruido o 
    recolectado por el garbage collector (recolector de basura).

    En términos simples, el metodo __del__() es el destructor de
    un objeto, y se utiliza para realizar tareas de limpieza cuando
    el objeto ya no es necesario, como liberar recursos o cerrar
    conexiones abiertas, archivos o base de datos.

    Para ello se crea un metodo dunder en la clase padre.
'''
class Persona:
    def __init__(self, nombre):
        self.nombre = nombre
        print(f"Persona {self.nombre} creada.")

    def __del__(self):
        print(f"Persona {self.nombre} eliminada.")

# Crear un objeto
p1 = Persona("Juan")

# Eliminar el objeto manualmente
del p1

# Salida esperada:
# Persona Juan creada.
# Persona Juan eliminada.
```

:fire: MRO

El método `mro()` (**Method Resolution Order**) en Python devuelve el orden en el que se buscan los métodos y atributos en una jerarquía de clases. Es útil cuando trabajas con **herencia múltiple**, ya que muestra el orden en que Python recorrerá las clases para encontrar un método o atributo

```python
class A:
    pass

class B(A):
    pass

class C(A):
    pass

# El orden en que definimos las clases extendidas es importante
class D(B, C):  # Herencia múltiple
    pass

print(D.mro())  # Muestra el orden de búsqueda

'''
    [<class '__main__.D'>, 
        <class '__main__.B'>, 
        <class '__main__.C'>, 
        <class '__main__.A'>, 
        <class 'object'>]

    Esto significa que cuando buscas un método en D, 
    Python seguirá este orden:

    1. D
    2. B
    3. C
    4. A
    5. object (clase base de todas las clases en Python)
'''
```

:fire: CLASE ABSTRACTA

Es una clase que no se puede instanciar directamente.
Es decir, no puedes crear un objeto de una clase abstracta, pero si
puede servir como base para otra clase. las clases abstractas son
útiles cuando queremos definir una estructura común que será heradada y complementada por clases derivadas.

Al crear un metodo abstracto toda la clase se transforma en abstracta, y obliga a las clases hijas a heredar metodos definidos.

```python
''' ABC
    Para crear una clase abstracta esta esta obligada a heredar de ABC 
    "Abstract Base Class". este modulo debe ser importado.

    1. se utiliza el decorador @abstractmethod para indicar que
        que el siguiente metodo sera abstracto, indicando que
        las clases hijas deben crear este metodo por obligacion.
    2. No se define cuerpo a los metodos abstractos ya que estos solo
        indican que son para su posterior implementacion.
'''
from abc import ABC, abstractmethod

class NomClase(ABC) # hereda de la clase ABC
    @abstractmethod
    def nom_metodo(self):
        pass
```

:fire: VARIABLE DE CLASE

Estas variables se asocian directamente con la clase, por lo tanto no se necesita una instancia para acceder al valor de la variable, solo necestiamos de la misma clase.

```python
class NomClase:
    # Accesible desde clase e instancia de esta
    nom_var_clase = valor

    def __init__(self, param):
        # accesible solo desde instancia
        self._varaible_instancia = param

# Acceder a la propiedad fuera de la clase
NomClase.nom_var_clase

# Definir una nueva variable de clase fuera de esta:
NomClase.nomVariable = valor
```

:fire: METODO ESTATICO DE CLASE

El decorador `@staticmethod` se usa para definir **métodos estáticos** dentro de una clase. A diferencia de los métodos de instancia (`self`) y los métodos de clase (`cls`), los métodos estáticos **no reciben ningún parámetro especial** y funcionan como funciones normales dentro de la clase.

- No reciven parametro self

- No pueden acceder a metodos/atributos de instancia o de la clase

```python
class Calculadora:
    @staticmethod
    def sumar(a, b):
        return a + b

print(Calculadora.sumar(5, 3))  # Salida: 8
```

:fire: METODO DE CLASE

El decorador `@classmethod` se usa para definir métodos de clase. A diferencia de los métodos de instancia (que reciben `self` como primer argumento), los métodos de clase reciben `cls`, que representa la propia **clase** en lugar de una instancia específica.

- No puede acceder a atributos/metodos de instancia

- Se puede acceder a atributos/metodos de clase

```python
class Ejemplo:
    atributo_clase = "Hola, soy un atributo de clase"

    @classmethod
    def mostrar(cls):
        # Accedemos a las variables de clase con cls.nom_atributo_clase
        return f"Accediendo a: {cls.atributo_clase}"

    @classmethod
    def __incrementar_contador(cls):  # Método de clase privado
        cls.__contador += 1

print(Ejemplo.mostrar())  # Se puede llamar sin crear una instancia

# Intentar acceder al método privado
print(Ejemplo.__incrementar_contador())  # AttributeError

''' Metodo de clase privado
    Si queremos un metodo de clase privado, podemos 
    combinar @classmethod con el prefijo __
'''
```

:fire: CONSTANTES DE CLASE

Por lo regular la definicion de estas constantes se crean en archivos de nombre config.py/constant.py

Aun asi, el valor de esta variable se puede modificar, es importante entender que si vemos esta convencion es indicativo de que no debemos modificar este dato.

```python
NOM_CONSTANTE = valor

--- en otro modulo ---
formo config impor NOM_CONSTANTE
```

:fire: METODOS ACCESIBLES SOLO DENTRO DE LA CLASE
En Python, un método se considera **privado** cuando su nombre comienza con **dos guiones bajos (`__`)**.

```python
class Ejemplo:
    def __init__(self, nombre):
        self.nombre = nombre  # Atributo público

    def __metodo_privado(self):
        return "Este método solo se puede usar dentro de la clase"

    def publico(self):
        return self.__metodo_privado()  # Se llama dentro de la clase

# Crear objeto
obj = Ejemplo("Python")

# Intentar acceder al método privado desde fuera
print(obj.publico())  # Se puede acceder porque es llamado dentro de la clase

print(obj.__metodo_privado())  # Error: AttributeError
```

:round_pushpin: METODOS PROTEGIDOS

Si solo quieres indicar que un método **no debería** usarse fuera de la clase (pero sigue siendo accesible), usa **un guion bajo (`_`)** al inicio.

```python
class Prueba:
    def _metodo_protegido(self):
        return "Puedo llamarse desde fuera, pero no debería"

obj = Prueba()
print(obj._metodo_protegido())  # ⚠️ Funciona, pero no es recomendado

'''
    Los métodos protegidos siguen siendo accesibles, 
    pero es una convención para que los programadores 
    sepan que no deben usarlos directamente.
'''
```

:fire: Notaciones hint

```python
class NomClase:

'''
    Puedes usar : tipo en los atributos de una clase 
    para indicar qué tipo de datos deben contener.
'''
    nom_var_clase: tipo_dato = valor


''' vehiculo: Vehiculo
    * vehiculo → Es el nombre del parámetro que recibe la función.
    * Vehiculo → Es una anotación de tipo (type hint), lo 
        que indica que el parámetro vehiculo debería ser una 
        instancia de la clase Vehiculo.

    * -> tipo_dato_retorno, indica el tipo de dato que sera
        retornado
'''
    def nom_clase(self, vehiculo: Vehiculo) -> tipo_dato_retorno
        pass
```

### HERENCIA

```python
class Padre:
    def __init__(self, parametro)
        self._parametro = parametro


''' Herencia
    Para que la herencia ocurra se debe indicar la siguiente
    sintanxis en la clase hija (ClasePadre) tambien podemos
    lograr herencia multiple (Clase1, Clase2).

    Si la clase padre posee atributos en el inicializador este
    debe inicializarse en la clase hija mediante: 
        super.__init__(parametros)
'''
class Hijo(Padre): # Herencia
    def __init__(self, parametro, parametro2):
        super().__init__(parametro) # Invocacion de clase metodo padre
        self._parametro2 = parametro2

    def nom_metodo(self):
        # llamada metodo padre
        super().nombre_metodo_padre()
```

### HERENCIA MULTIPLE

```python
'''
    Cuando la herencia es multiple, es mejor llamar a las
    clases padre dentro del inicializador de la clase hija,
    para asi diferenciar uno de otro.
'''
class NomClase(Padre1, Padre2):
    def __init__(self, parametro1, parametro2, parametro3):
        self.nom_atributo = parametro1
        # Inicializadores de clases padre
        Padre1.__init__(self, parametro2)
        Padre2.__init__(self, parametro3)

    def nom_metodo(self, param):
        '''
            Se debe pasar self explícitamente 
            porque los métodos de instancia en Python 
            esperan que el primer parámetro sea la instancia de la clase.
        '''
        Padre1.nom_metodo(self, param)
```

### SOBREESCRITURA

Basicamente son los metodos de clases padres sobreescritos en clases hija.

```python
class Padre:
    def __init__(self, param):
        self._param = param

    def __str__(self):
        return self._param

class Hija(Padre):
    def __init__(self, param1, param2):
        super().__init__(param1)
        self._param2 = param2

    # Sobreescritura del metodo padre
    def __str__(self):
        # llamando metodo de clase padre
        return f'{super().__str__()} {self._parametro2}' 
```

### POLIMORFISMO

El polimorfismo en Python (y en programación orientada a objetos en general) es un principio que permite que diferentes clases tengan métodos con el mismo nombre, pero con comportamientos diferentes según la clase que los invoque. Esto permite que una misma acción (como llamara un método) se ejecute de manera distinta dependiendo del tipo de objeto que lo invoca.

Ejemplo de polimorfismo por herencia:
Imaginemos que tienes una clase base llamada Animal, y
varias clases hijas como Perro y Gato, que sobrescriben
un método común llamado hacer_sonido.

```python
class Animal:
    def hacer_sonido(self):
        raise NotImplementedError("Este método debe ser implementado por la subclase")

class Perro(Animal):
    def hacer_sonido(self):
        return "Guau!"

class Gato(Animal):
    def hacer_sonido(self):
        return "Miau"

# Usando el polimorfismo
def hacer_sonido_del_animal(animal):
    print(animal.hacer_sonido())

# Crear instancias de las clases
perro = Perro()
gato = Gato()

# Llamamos al método de los dos animales
hacer_sonido_del_animal(perro)  # Salida: Guau!
hacer_sonido_del_animal(gato)   # Salida: Miau
```

### SOBRECARGA DE OPERADORES

La sobrecarga de operadores en Python es un concepto que permite a los programadores personalizar el comportamiento de los operadores estándar (como `+`, `-`, `*`, etc.) para objetos de clases propias.

Esto significa que puedes definir cómo deben comportarse los operadores cuando se utilizan con instancias de tus clases.

En lugar de que un operador tenga un significado fijo (por ejemplo, la suma para números), puedes definir su comportamiento para tus propias clases. Así, por ejemplo, podrías sumar dos objetos de una clase específica y determinar qué sucede en ese caso.

#### **Métodos Especiales para Sobrecarga de Operadores**

Para lograr esto, Python utiliza **métodos especiales** o **mágicos** (también llamados *dunder methods*, por sus nombres que comienzan y terminan con doble guion bajo `__`).

Algunos ejemplos comunes de estos métodos son:

- `__add__(self, other)`: Para el operador `+`.
- `__sub__(self, other)`: Para el operador `-`.
- `__mul__(self, other)`: Para el operador `*`.
- `__eq__(self, other)`: Para el operador `==`.
- `__lt__(self, other)`: Para el operador `<`.

```python
'''
    Imagina que tenemos una clase Punto que 
    representa puntos en un plano cartesiano. Queremos 
    sobrecargar el operador + para que sume las coordenadas de dos puntos.
'''
class Punto:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __add__(self, otro):
        # Sobrecargamos el operador '+' para sumar dos puntos
        if isinstance(otro, Punto):
            return Punto(self.x + otro.x, self.y + otro.y)
        return NotImplemented

    def __repr__(self):
        return f"Punto({self.x}, {self.y})"

# Crear dos puntos
p1 = Punto(1, 2)
p2 = Punto(3, 4)

# Sumar los dos puntos
p3 = p1 + p2
print(p3)  # Salida: Punto(4, 6)
```
