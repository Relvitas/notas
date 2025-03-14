## CONSUMIR API

Para hacer solicitudes HTTP y consumir APIs se utilizan dos bibliotecas populares.

### Requests

Requests es una biblioteca de Python que permite realizar solicitudes HTTP de una manera sencilla y amigable. Se considera la biblioteca de facto para hacer solicitudes HTTP en Python debido a su facilidad de uso y su sintaxis clara.

1. Instalar libreria
   
   `pip install requests`

2. Importar libreria
   
   `import requests`

### Metodos

:fire: **requests.get()**

Esta funcion realiza solicitudes HTTP GET.

```python
'''
    response: se convierte en un objeto.
'''

# Definir la URL a la que se va a hacer la solicitud GET
url = 'http://httpbin.org/get'

response = requests.get(url)
```

:round_pushpin: **decode('utf-8')**

Metodo correspondiente a los objetos de typo bytes en python. Cuando recibimos datos en formato binario (bytes), como una respuesta HTTP de response.content. podemos utilizar el metodo decode() para convertir esos bytes en una cadena de texto legible utilizando la codigificacion utf-8

```python
print(r.content.decode('utf-8'))


# ============== SALIDA =========== #
{
  "args": {}, 
  "headers": {
    "Accept": "*/*", 
    "Accept-Encoding": "gzip, deflate", 
    "Host": "httpbin.org", 
    "User-Agent": "python-requests/2.32.3", 
    "X-Amzn-Trace-Id": "Root=1-67cc6c85-26831c2e1b84e63812a4a99b"
  }, 
  "origin": "177.93.52.72", 
  "url": "http://httpbin.org/get"
}
```

:round_pushpin: **Pasar parametros en la URL para GET**

Cuando queremos enviar algun tipo de dato para que este nos devuelva informacion especifica se tienen dos sintaxis:

```python
'''
    Sintaxis manual:
    En donde pasamos key=value directamente a la url
    importante se agrega ? al primer parametro ?key=value si es
    un segundo parametro este se hace con &key=value
'''
r = requests.get('http://httpbin.org/get?nombre=eduardo&curso=python')

'''
    Sintaxis con diccionario
    Construimos un diccionario con (key: valor), estos seran
    los parametros de consulta de este, a la consulta
    le agregamos , params=diccionario
'''
args = {
    'nombre': 'eduardo',
    'curso': 'python' 
}

r = requests.get('http://httpbin.org/get', params=args)

'''
    Estos los vermenos reflejado en la key "args", de nuestra
    peticion GET
'''
# ============== SALIDA =========== #
{
  "args": {
    "curso": "python", 
    "nombre": "eduardo"
  }, 
  "headers": {
    "Accept": "*/*", 
    "Accept-Encoding": "gzip, deflate", 
    "Host": "httpbin.org", 
    "User-Agent": "python-requests/2.32.3", 
    "X-Amzn-Trace-Id": "Root=1-67cc732b-5c46320a214ba9d610d9a56a"
  }, 
  "origin": "177.93.52.78", 
  "url": "http://httpbin.org/get?nombre=eduardo&curso=python"
}

# ============== HEADERS =========== #
'''
    Con este enviamos informacion adicional al servidor
        cuando hacemos una solicitud HTTP. los headers
        son parte de la solicitud http y permiten enviar
        metadatos, como el tipo de contenido que esperamos
        recibir, la autenticacin, el agente de usuario etc.

    User-Agent: Identifica el cliente que está 
        haciendo la solicitud. Algunos servidores pueden 
        requerir un User-Agent específico para permitir el acceso.

    Authorization: Se utiliza para enviar credenciales 
        de autenticación, como un token Bearer.

    Content-Type: Aunque es más común en solicitudes 
        POST o PUT, también puede ser útil en GET para 
        indicar el tipo de contenido que estás enviando 
        (aunque en GET no suele ser necesario).

    Accept: Indica al servidor qué tipo de contenido puede 
        manejar el cliente. Por ejemplo, si esperas una 
        respuesta en formato JSON, puedes especificarlo así:
'''
# Definir los headers que quieres enviar
headers = {
    'User-Agent': 'MiAplicacion/1.0',
    'Accept': 'application/json',
    'Authorization': 'Bearer tu_token_aqui',
    'Content-Type': 'application/json'
}

# Hacer la solicitud GET con los headers
response = requests.get('https://api.ejemplo.com/endpoint', headers=headers)

# Imprimir la respuesta
print(response.json())

# stream=True
'''
    Util para cuando se trabajan con archivos grandes o cuando
    no queremos descargar todo el contenido.

    Normalmente, cuando haces una solicitud con requests.get(), 
    la librería descarga todo el contenido de la respuesta 
    de una vez y lo guarda en la memoria. Esto está bien 
    para archivos pequeños, pero si estás descargando un 
    archivo grande (como un video o una imagen), podrías 
    quedarte sin memoria.

    Con stream=True, le dices a requests que no descargue 
    todo el contenido de inmediato, sino que lo 
    haga en "pedacitos" (o "streaming"). Esto te permite 
    procesar el contenido poco a poco, 
    sin ocupar toda tu memoria.
'''
response = requests.get(url, stream=True)
requests.close() # cerrar la conexion
```

```python
'''
    Usa response.iter_lines() para leer el 
    contenido línea por línea.

    El método iter_content() te permite leer el contenido 
    de la respuesta en "pedacitos" (o "chunks"). 
    Puedes especificar el tamaño de cada pedacito 
    con el parámetro chunk_size. Por ejemplo:

    * chunk_size=1024: Lee 1 KB a la vez.   
    * chunk_size=8192: Lee 8 KB a la vez.
'''

import requests

# URL del video
url = 'https://ejemplo.com/video_grande.mp4'

# Hacer la solicitud GET con stream=True
response = requests.get(url, stream=True)

# Verificar si la solicitud fue exitosa
if response.status_code == 200:
    # Abrir un archivo en modo binario para guardar el video
    with open('video_grande.mp4', 'wb') as archivo:
        # Leer el contenido en "pedacitos" y escribirlo en el archivo
        for chunk in response.iter_content(chunk_size=8192):
            if chunk:  # Filtrar chunks vacíos
                archivo.write(chunk)
    print("¡Video descargado con éxito!")
else:
    print(f"Error: {response.status_code}")
```

:fire:**requests.post()**

Enviar información.

```python
r = requests.post(
    'https://httpbin.org/post', 
    data={'key': 'value'}
)
```

:fire: **requests.put()**

Actualizar un recurso

```python
r = requests.put(
    'https://httpbin.org/put', 
    data={'key': 'value'}
)
```

:fire: **requests.delete()**

Eliminar un recurso

```python
r = requests.delete('https://httpbin.org/delete')
```

:fire: **requests.head()**

Consultar la existencia de un recurso

```python
r = requests.head('https://httpbin.org/get')
```

:fire: **requests.options()**

Lo utilizan los navegadores de forma predeterminada

```python
r = requests.options('https://httpbin.org/get')
```

### POST

El método **POST** es como decirle al servidor: "Oye, quiero **crear** algo nuevo". Por ejemplo, si tienes una lista de juguetes y quieres agregar uno nuevo, usas `POST` para decirle al servidor que guarde la información del nuevo juguete.

- **Crear cosas nuevas**: Por ejemplo, agregar un nuevo juguete, un nuevo usuario, o un nuevo mensaje.

- **Enviar datos al servidor**: Puedes enviar información como formularios, archivos, o cualquier cosa que el servidor necesite para crear algo nuevo.

```python
'''
    * json -> lo que hace es transformar un diccionario en formato
        json que contendra los valores que enviaremos al servidor.

    * data -> si colocamos el diccionario dentro de este parametro
        toda la informacion sera enviada dentro de form

        En general este se utiliza cuando enviamos infomracion
        codificada de un formulario HTML.

        A este tambien se le puede pasar una lista de tuplas
        o un diccionario con listas como valores. esto
        es util cuando la forma tiene varios elementos que
        usa la misma clave.

        playload_typles [
            ('key1', 'value1'),
            ('key1', 'value2')
        ]

        payload_dic {
            'key': ['value1', 'value2']
        }

##### print
{
  ...
  "form": {
    "key1": [
      "value1",
      "value2"
    ]
  },
  ...
}

    Esta información que enviamos es vista en la seccion data,
    dentro del json

    si queremos que el parametro data=dic se convierta en la
    seccion data y no en form este se debe serializar
    con data=json.dumps(diccionario)
'''
payload={'ket':'valor'}
requests.post(url, json=payload)
```

### PUT

Es como decirle al servidor: "Oye, quiero **actualizar** algo que ya existe". Por ejemplo, si tienes un juguete y quieres cambiarle las pilas, usas `PUT` para decirle al servidor que actualice la información del juguete.

```python
import requests

# URL del juguete que quieres actualizar
url = 'https://api.ejemplo.com/juguetes/1'

# Los nuevos datos que quieres poner en el juguete
datos_actualizados = {
    'nombre': 'Super Coche',
    'color': 'rojo'
}

# Headers para decirle al servidor que estamos enviando datos en formato JSON
headers = {
    'Content-Type': 'application/json'
}

# Hacer la solicitud PUT para actualizar el juguete
response = requests.put(url, json=datos_actualizados, headers=headers)

# Verificar si la actualización fue exitosa
if response.status_code == 200:
    print("¡El juguete se actualizó correctamente!")
else:
    print(f"Algo salió mal. Código de error: {response.status_code}")
```

### DELETE

Es como decirle al servidor: "Oye, quiero **borrar** algo que ya no necesito". Por ejemplo, si tienes un juguete roto y ya no lo quieres, usas `DELETE` para decirle al servidor que lo elimine.

```python
import requests

# URL del juguete que quieres borrar
# Se le dice al servidor que queremos borrar el juguete con id 1
url = 'https://api.ejemplo.com/juguetes/1'

# Hacer la solicitud DELETE para borrar el juguete
response = requests.delete(url)

# Verificar si el borrado fue exitoso
if response.status_code == 200:
    print("¡El juguete se borró correctamente!")
else:
    print(f"Algo salió mal. Código de error: {response.status_code}")
```

### ATRIBUTOS

:fire: **.status_code**

Este atributo almacena el codigo de estatus de la peticion GET

```python
r.status_code
```

:fire: **.enconding**

```python
'''
    * Permite validar el formato de codificacion en la que viene
        un archivo.

    * Tambien podemos cambiar la codificacion de este.
'''
r.encoding = 'utf-8'
```

:fire: **.content**

Acceder al contenido de una respuesta.

```python
'''
    * Devuelve el contenido de la respuesta en bytes crudos
    * Es útil cuando estamos trabajando con datos binarios
        como imagenes, archivos descargados, o cualquier
        otro contenido no textual.

    * No realiza ninguna decodificación del contenido
'''
r.content
```

:fire: **.text**

Acceder al contenido de una respuesta

```python
'''
    * Devuelve el contenido de la respuesta ya decodificado
        en cadena de texto (string)

    * La decodificación se hace utiliza que se especifica en
        el encabezado "Content-Type" de la respuesta
        (o la codificacion que se establece explisitamente)
        usando .encoding
'''
r.text
```

:fire: **.json()**

Decodificar json en caso de que se esten tratando datos tipo JSON

```python
'''
    Este metodo convierte un json en un diccionario
'''
r = r.json()
```

:fire: **.headers**

Obtener todos los encabezados de respuesta del servidor

```python
response_headers = r.headers
```

:fire: **response.cookies**

Las cookies que se envían o reciben en una solicitud HTTP. Puedes usarlo para:

1. **Enviar cookies** al servidor en una solicitud.

2. **Recibir cookies** del servidor en una respuesta.

:round_pushpin: **Enviar cookies al servidor**

```python
'''
    Si quieres enviar cookies al servidor, puedes pasar un 
    diccionario de cookies al parámetro cookies de una 
    solicitud (get, post, etc.).
'''
import requests

# Cookies que quieres enviar
mis_cookies = {
    'session_id': '123456',
    'usuario': 'pikachu'
}´

# Hacer una solicitud GET con cookies
response = requests.get('https://ejemplo.com', cookies=mis_cookies)

# Verificar la respuesta
print(response.status_code)

## QUE HACE
'''
    Envía las cookies session_id y usuario al servidor.
    El servidor puede usar estas cookies para identificar 
    al usuario o mantener su sesión.
'''
```

:round_pushpin: **Recibir cookies del servidor**

Cuando haces una solicitud, el servidor puede enviar cookies en la respuesta. Puedes acceder a estas cookies a través del atributo `.cookies` del objeto `response`.

```python
import requests

# Hacer una solicitud GET
response = requests.get('https://ejemplo.com')

# Obtener las cookies de la respuesta
cookies_recibidas = response.cookies

# Mostrar las cookies
print("Cookies recibidas:", cookies_recibidas)

## QUE HACE
'''
    Hace una solicitud GET a https://ejemplo.com.
    Accede a las cookies que el servidor envió en la respuesta.
    Muestra las cookies en la termina
'''
```

:fire: **requests.session()**

Si estás haciendo múltiples solicitudes a un servidor y necesitas mantener las cookies entre solicitudes (por ejemplo, para mantener una sesión), puedes usar un objeto `Session` de `requests`.

```python
import requests

# Crear una sesión
session = requests.Session()

# Hacer una solicitud GET para obtener cookies iniciales
response = session.get('https://ejemplo.com/login')
print("Cookies iniciales:", session.cookies)

# Hacer otra solicitud (las cookies se mantienen)
response = session.get('https://ejemplo.com/dashboard')
print("Cookies después del dashboard:", session.cookies)

## QUE HACE 
'''
    Crea una sesión con requests.Session().
    Las cookies se almacenan automáticamente en la sesión 
    y se envían en cada solicitud posterior.

    Esto es útil para mantener la sesión del usuario en un sitio web.
'''
```

:round_pushpin: Acceder a valores especificos de las cookies

Si quieres acceder a un valor específico de una cookie, puedes tratarla como un diccionario.

```python
import requests

# Hacer una solicitud GET
response = requests.get('https://ejemplo.com')

# Obtener una cookie específica
valor_cookie = response.cookies.get('nombre_de_la_cookie')
print("Valor de la cookie:", valor_cookie)
```

:round_pushpin: Eliminar o modificar cookies

Puedes modificar o eliminar cookies en una sesión o en una solicitud específica.

```python
import requests

# Crear una sesión
session = requests.Session()

# Agregar una cookie manualmente
session.cookies.set('mi_cookie', 'valor123')

# Eliminar una cookie
session.cookies.clear('mi_cookie')
```

:round_pushpin: **sessiones.auth**

Se usa para establecer credenciales de autenticación (como un nombre de usuario y una contraseña) que se enviarán automáticamente en cada solicitud.

```python
import requests
from requests.auth import HTTPBasicAuth

# Crear una sesión
session = requests.Session()

# Configurar la autenticación básica
session.auth = ('usuario', 'contraseña')

# Hacer una solicitud GET a un endpoint protegido
response = session.get('https://api.ejemplo.com/protegido')
# Tambien podemos hacerlo en una sola linea


# Verificar la respuesta
if response.status_code == 200:
    print("Acceso concedido:")
    print(response.json())
else:
    print(f"Error: {response.status_code}")


## QUE HACE 
'''
    Crea una sesión con requests.Session().

    Configura la autenticación básica 
    usando session.auth con un nombre de usuario y una contraseña.

    Hace una solicitud GET a un endpoint protegido. 
    Las credenciales se envían automáticamente.

    Verifica si la solicitud fue exitosa (código 200) 
    y muestra la respuesta.
'''
```

---

### urllib2

urllib2 es una biblioteca estándar de Python que permite hacer solicitudes HTTP. Aunque es parte de la biblioteca estándar y no requiere instalación adicional, su sintaxis puede ser un poco más compleja en comparación con Requests. Cabe mencionar que en Python 3, urllib2 fue dividida en varios módulos bajo el nombre de urllib.

En Python 3, `urllib2` ya no existe como un único módulo; en su lugar, se dividió en varios módulos bajo el nombre de `urllib`. 

httpbin.org
