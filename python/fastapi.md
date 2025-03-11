## FastAPI

FastAPI es un moderno framework web para la construcción de aplicaciones APIs en Python, diseñado para ser rápido (de ahí su nombre), fácil de usar y eficiente. Está basado en los estándares de OpenAPI y JSON Schema, lo que facilita la creación de API RESTful robustas y de alto rendimiento.

:round_pushpin: **endpoint**

Es una URL (o dirección web) que actúa como un punto de acceso a un recurso o funcionalidad especificos dentro de la aplicación. En otras palabras, un endpoint es una "puerta de entrada" a través de la cual se puden enviar solicitudes (como consultas o acciones) a la aplicación web y recibir respuestas.

**Conceptos clave:**

1. **Ruta**: La URL que se utiliza para acceder al endpoint. Por ejemplo, en el código que me mostraste, `/` y `/items/{item_id}` son rutas.

2. **Método HTTP**: Los endpoints suelen estar asociados con métodos HTTP como GET, POST, PUT, DELETE, etc. Estos métodos determinan el tipo de operación que se realiza en el endpoint. En tu código, los métodos son `@app.get("/")` y `@app.get("/items/{item_id}")`, que indican que ambos endpoints responden a solicitudes HTTP GET.

3. **Función asociada**: Cada endpoint está asociado con una función específica en el código que se ejecuta cuando se accede a esa URL. Por ejemplo, `read_root` y `read_item` son las funciones asociadas a los endpoints en tu código.

## Instalación

1. Ejecutar en un entorno virtual
   
   Se agregan las comillas para que este funcione en cualquier terminal
   
   ```python
   pip install "fastapi[standard]"
   ```

2. Crear un archivo `main.py` con el siguiente contenido:
   
   ```python
   from typing import Union
   
   # se importa la libreria
   from fastapi import FastAPI
   
   # crea el app
   app = FastAPI()
   
   @app.get("/")
    def read_root():
    return {"Hello": "World"}
   
   @app.get("/items/{item_id}")
    def read_item(item_id: int, q: Union[str, None] = None):
    return {"item_id": item_id, "q": q}
   ```

3. Ejecutar el servidor local
   
   `fastapi dev main.py`

4. Validar si el servidor esta funcionando
   
    http://127.0.0.1:8000/items/5?q=somequery
   
   Veremos una respuesta como la siguiente
   
   ```python
   {"item_id": 5, "q": "somequery"}
   ```

5. FInalizar servicio
