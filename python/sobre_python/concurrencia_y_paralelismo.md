## Concurrencia y paralelismo

Cuando creamos una aplicación, el manejo de tareas puede ser sencillo con pocos usuarios. Sin embargo, a medida que la aplicación gana popularidad, la gestión de un número creciente de solicitudes se complica. ¿Cómo podemos solucionar esto? A través de técnicas de **paralelismo** y **concurrencia**. Estas técnicas permiten una administración más eficiente de las tareas, especialmente en situaciones donde se requiere procesar múltiples operaciones de forma simultánea.

:fire: Implementacion de concurrencia

```python
'''
    En Python, la librería threading nos permite 
    introducir concurrencia a través de hilos. 
    A continuación, se muestra un ejemplo de cómo realizar esto.

    En este código, se simulan las solicitudes 
    aplicando espera de tres segundos para demostrar 
    el procesamiento concurrente.
'''
import threading
import time

def procesar_solicitud(request_id):
    print(f"Procesando solicitud {request_id}")
    time.sleep(3)
    print(f"Solicitud {request_id} completada")

hilos = []
for i in range(3):
    hilo = threading.Thread(target=procesar_solicitud, args=(i,))
    hilos.append(hilo)
    hilo.start()

for hilo in hilos:
    hilo.join()

print("Todas las solicitudes completadas")
```

:round_pushpin: Evitar Deadloock

Un **deadlock** ocurre cuando dos o más hilos se bloquean mutuamente al esperar por un recurso que está siendo utilizado por otro hilo. Para evitar esto, podemos usar `RLock` en lugar de `Lock`.

```python
'''
    Usamos RLock para evitar que múltiples operaciones 
    simultáneas en una cuenta causen bloqueos.
'''
import threading

class CuentaBancaria:
    def __init__(self, saldo):
        self.saldo = saldo
        self.lock = threading.RLock()

    def transferir(self, otra_cuenta, cantidad):
        with self.lock:
            self.saldo -= cantidad
            otra_cuenta.depositar(cantidad)

    def depositar(self, cantidad):
        with self.lock:
            self.saldo += cantidad

cuenta1 = CuentaBancaria(500)
cuenta2 = CuentaBancaria(300)

hilo1 = threading.Thread(target=cuenta1.transferir, args=(cuenta2, 200))
hilo2 = threading.Thread(target=cuenta2.transferir, args=(cuenta1, 100))

hilo1.start()
hilo2.start()

hilo1.join()
hilo2.join()

print(f"Saldo cuenta1: {cuenta1.saldo}")
print(f"Saldo cuenta2: {cuenta2.saldo}")
```

:round_pushpin: Sincronizacion de hilos

Cuando varios hilos intentan acceder a un mismo recurso al mismo tiempo, pueden ocurrir problemas de coherencia. Para evitar esto, se utilizan mecanismos de **sincronización**, como `Lock` y `RLock`, que garantizan que solo un hilo acceda a un recurso crítico a la vez.

```python
'''
    El uso de Lock asegura que solo un hilo 
    modifique la variable saldo en un momento dado, 
    evitando que el resultado final sea incorrecto.
'''
import threading

# Variable compartida
saldo = 0
lock = threading.Lock()  # Crear un Lock

def depositar(dinero):
    global saldo
    for _ in range(100000):
        with lock:  # Bloquear el acceso para evitar condiciones de carrera
            saldo += dinero

hilos = []
for _ in range(2):
    hilo = threading.Thread(target=depositar, args=(1,))
    hilos.append(hilo)
    hilo.start()

for hilo in hilos:
    hilo.join()

print(f"Saldo final: {saldo}")  # Esperamos ver 200000 como saldo
```

:fire: async

En el contexto de Python, el asincronismo se implementa mediante corrutinas—funciones que pueden detenerse y reanudarse más tarde. Esto se logra gracias a las palabras clave `async` y `await`, y la librería `asyncio` que se encarga de gestionar el "event loop", un ciclo que maneja las tareas asíncronas y devuelve las respuestas eficientemente.

Para crear funciones asíncronas en Python, es fundamental seguir ciertos pasos y utilizar las herramientas adecuadas del lenguaje. A continuación, se presenta una guía práctica para definir una función asíncrona básica:

```python
'''
    1. Importar asyncio: Esta librería es esencial 
        para ejecutar funciones asíncronas y gestionar el event loop.

    2. Definir la función con async: Utilizamos la palabra 
        reservada async para indicar que la función es asíncrona.

    3. Simular espera con await: Empleamos await junto con 
        asyncio.sleep() para simular el tiempo de espera sin 
        afectar el event loop.

    4. Retornar un resultado: Después del procesamiento,
        podemos retornar un resultado, en este caso, 
        data multiplicado por dos.

    5. Definir una función principal asíncrona: 
        Esta función, denominada main, es donde se 
        inician las corrutinas. No recibe parámetros.

    6. Ejecutar el event loop: Utilizamos asyncio.run() 
        para iniciar el loop llamando a main, nuestra función principal.
'''

import asyncio

async def process_data(data):
    print(f"procesando {data}...")
    await asyncio.sleep(10)
    print(f"{data} ya terminó de procesarse.")
    return data * 2

async def main():
    print("inicio de procesamiento")
    result = await process_data("archivo.txt")
    print(f"resultado final: {result}")

asyncio.run(main())
```

:fire: Implentacion de paralelismo

```python
'''
    Para implementar paralelismo, utilizamos multiprocessing, 
    que permite la ejecución de procesos de manera paralela. 
    Aquí tienes un ejemplo básico para calcular el cuadrado 
    de números de forma simultánea:

    El uso del pool.map en el ejemplo asegura 
    que cada número se procese en paralelo, proporcionando 
    resultados inmediatos.
'''
import multiprocessing

def calcular_cuadrado(n):
    return n * n

if __name__ == "__main__":
    numeros = [1, 2, 3, 4, 5]
    with multiprocessing.Pool() as pool:
        resultados = pool.map(calcular_cuadrado, numeros)
    print(resultados)
```

:round_pushpin: Coordinacion de tareas con multiprocessing.Manager

Cuando los procesos deben compartir estructuras de datos complejas (como listas o diccionarios), podemos usar un **Manager** para crear un espacio de memoria compartido entre procesos.

```python
'''
    multiprocessing.Manager nos permite 
    crear una lista compartida entre varios procesos, 
    facilitando la comunicación entre ellos.
'''
import multiprocessing

def agregar_valores(lista_compartida):
    for i in range(5):
        lista_compartida.append(i)

if __name__ == "__main__":
    with multiprocessing.Manager() as manager:
        lista_compartida = manager.list()

        proceso1 = multiprocessing.Process(target=agregar_valores, args=(lista_compartida,))
        proceso2 = multiprocessing.Process(target=agregar_valores, args=(lista_compartida,))

        proceso1.start()
        proceso2.start()

        proceso1.join()
        proceso2.join()

        print(f"Lista compartida: {lista_compartida}")
```

:round_pushpin: Compartir datos entre procesos multiprocessing.Queue

A diferencia de los hilos, los procesos no comparten memoria de forma predeterminada. Para que dos procesos puedan compartir datos, Python proporciona herramientas como `multiprocessing.Queue` y `multiprocessing.Value`.

```python
'''
    Usamos Queue para que el proceso secundario 
    pueda pasar datos de vuelta al proceso principal.
'''
import multiprocessing

def calcular_cuadrado(numeros, cola):
    for n in numeros:
        cola.put(n * n)

if __name__ == "__main__":
    numeros = [1, 2, 3, 4, 5]
    cola = multiprocessing.Queue()

    proceso = multiprocessing.Process(target=calcular_cuadrado, args=(numeros, cola))
    proceso.start()
    proceso.join()

    # Extraer resultados de la cola
    while not cola.empty():
        print(cola.get())
```
