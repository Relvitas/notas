## API

Una **API** (Interfaz de Programación de Aplicaciones, por sus siglas en inglés: Application Programming Interface) es un conjunto de definiciones y protocolos que permiten la comunicación entre diferentes sistemas de software. Las APIs permiten a los desarrolladores interactuar con los servicios y datos de otros programas de una manera estructurada y segura.

### Tipos de APIs

- **APIs Web**: Permiten la interacción con servicios y recursos a través de la web, utilizando protocolos como HTTP/HTTPS.

- **APIs de Sistema**: Interactúan con el sistema operativo para realizar tareas como la gestión de archivos o procesos.

- **APIs de Biblioteca**: Facilitan el uso de bibliotecas de software proporcionando funciones predefinidas que los desarrolladores pueden invocar.

### HTTP

El protocolo HTTP (Hypertext Transfer Protocol) es el protocolo de comunicación fundamental utilizado en la World Wide Web para la transferencia de datos. Este protocolo define cómo se deben estructurar y transmitir los mensajes entre los navegadores web (clientes) y los servidores web. HTTP es un protocolo de texto sin estado, lo que significa que cada solicitud y respuesta son independientes, y el servidor no guarda información sobre las solicitudes anteriores.

### Conceptos Clave de HTTP

1. **Cliente y Servidor**: El cliente (como un navegador web) envía una solicitud HTTP al servidor, que procesa la solicitud y envía una respuesta HTTP de vuelta al cliente.

2. **Métodos HTTP**: HTTP define varios métodos que indican la acción a realizar sobre el recurso identificado por el URL. Los métodos más comunes son:
   
   - **GET**: Solicita la representación de un recurso específico. Las solicitudes GET solo recuperan datos.
   
   - **POST**: Envia datos al servidor para crear o actualizar un recurso.
   
   - **PUT**: Envia datos al servidor para actualizar o crear un recurso.
   
   - **DELETE**: Elimina un recurso específico.
   
   - **HEAD**: Similar a GET, pero solo solicita los encabezados de la respuesta.
   
   - **OPTIONS**: Describe las opciones de comunicación para el recurso de destino.

3. **URLs**: Los URLs (Uniform Resource Locators) especifican la dirección del recurso en la web. Un URL típico se ve así: `http://www.ejemplo.com/pagina`.

4. **Códigos de Estado**: Los servidores responden a las solicitudes HTTP con códigos de estado que indican el resultado de la solicitud. Algunos ejemplos comunes son:
   
   - **200 OK**: La solicitud se ha completado con éxito.
   
   - **404 Not Found**: El recurso solicitado no se ha encontrado.
   
   - **500 Internal Server Error**: El servidor ha encontrado un error al procesar la solicitud.

5. **Encabezados HTTP**: Las solicitudes y respuestas HTTP incluyen encabezados que proporcionan información adicional sobre la transacción. Por ejemplo, los encabezados pueden especificar el tipo de contenido, la longitud del contenido, la codificación y más.

### PETICIÓN HTTP

```python
'''
    Metodo_HTTP <path/ruta de peticion> <version del protocolo>
    <encabezados>
'''
GET /index.html HTTP/1.1 # Identifica el tipo de petición
Host: www.example.com
Referer: www.google.com
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
```

:fire: **Métodos/Verbos**

Identifican que tipo de peticion esta realizando el cliente hacia el servidor

```python
'''
    GET (Obtener información): Sirve para solicitar al 
        servidor que me envie información.
    POST: Sirve para enviar información desde el cliente hacia el
        servidor.
    PUT: Sirve para actualizar un recurso.
    DELETE: Sirve para eliminar un recurso.
    PATCH: Sirve para actualizar un recurso pero en forma pequeña, es
        decir un pedacito del recurso.
    HEADER: Sirve para consultar la existencia de un recurso.
    OPTIONS: Lo utilizan los navegadores de forma nativa.
'''
```

:fire: **Idempotencia**

La idempotencia es una propiedad de ciertos sistemas y operaciones que garantiza que realizar la misma operación varias veces tiene el mismo efecto que realizarla una sola vez. En otras palabras, una operación idempotente produce el mismo resultado sin importar cuántas veces se ejecute.

**Metodos idempotente**

En el contexto de HTTP, ciertos métodos son idempotentes, lo que significa que realizar varias solicitudes idénticas tendrá el mismo efecto que realizar una sola solicitud.

- **GET**: Obtener un recurso es idempotente. Si solicitas la misma página web varias veces, obtendrás la misma respuesta sin causar efectos secundarios.

- **PUT**: Actualizar un recurso es idempotente. Si envías la misma actualización varias veces, el recurso se actualizará de la misma manera y no habrá cambios adicionales.

- **DELETE**: Eliminar un recurso es idempotente. Si intentas eliminar un recurso que ya ha sido eliminado, no ocurrirá ningún cambio adicional.

**Metodo no idempotente**

* **POST**: Enviar datos a un servidor para crear un nuevo recurso no es idempotente. Enviar varias solicitudes POST puede resultar en la creación de múltiples recursos.

### RESPUESTA HTTP

```python
#  <version_http> <codigo_de_respuesta> <texto_del_codigo>
HTTP/1.1 200 OK
# Encabezados de respuesta
Date: Mon, 27 Jul 2020 12:28:53 GMT
Server: Apache/2.4.1 (Unix)
Last-Modified: Wed, 22 Jul 2020 19:15:56 GMT
Content-Type: text/html
Content-Length: 88

# Cuerpo de respuesta
<html>
<body>
<h1>¡Hola, Mundo!</h1>
(Contenido)
.
.
</body>
</html>
```

:fire: **Codigos de respuesta**

Documentación [MDN]([Códigos de estado de respuesta HTTP - HTTP | MDN](https://developer.mozilla.org/es/docs/Web/HTTP/Status))

```python
'''
    100 a 199: Son informativos,
        Es información como me estoy conectando ya me conecte,
        estos codigos en general no los vamos a utilizar dado
        a que los maneja la libreria.

    200 a 299: Correcto,
        Cuando una peticion se realiza correctamente y todo
        Salio bien.

    300 a 399: Redireccion,
        Cuando un servidor web responde a una solicitud 
        indicando que el recurso solicitado se encuentra 
        en una ubicación diferente.

    400 a 499: Error del cliente
        Ocurren cuando por ejemplo el cliente hace una
        peticion mal.

    500 a 599: Error del servidor
        Ejemplo cuando se cae la base de datos. son errores
        del servidor y no del cliente.
'''
```

### REST (Representational State Transfer)

Propiedades rest.

Todo es un recurso y debe:

* Tener un identificador unico (URI)
  
  ```python
  '''
      Esas se pueden identificar con [url|urn]
          url: localizador del recurso.
              https://www.example.com/pagina -> Indica donde se
                  encuentra un recurso y cómo acceder a él.
  
          urn: nombre del recurso -> es muy poco utilizado
              urn:isbn:0451450523 -> Proporciona un identificador
                 unico para un recurso, sin indicar su localizacion.
  '''
  ```

* Estar representado por un formato (XML, JSON, JPEG, etc)

* Poderse representar con diferentes formatos

* las comunicaciones no tienen estado
  
  Es decir que estas comunicaciones no recuerdan una comunicacion anterior.

### CONTENT-TYPE

Estos son solo algunos de los fomratos

* text/plain

* text/html

* text/xml

* application/json

* image/jpeg

* image/png

## HATEOAS

HATEOAS (Hypermedia as the Engine of Application State) es un principio de diseño dentro de la arquitectura REST (Representational State Transfer) que promueve el uso de hipermedios para permitir a los clientes navegar por las API de una manera dinámica y autodocumentada. Es un componente clave para crear APIs RESTful verdaderamente intuitivas y flexibles.

### Conceptos Clave de HATEOAS

1. **Hypermedia**: Se refiere a los enlaces dentro de las respuestas de las API que permiten a los clientes descubrir y navegar por los recursos de manera dinámica. Estos enlaces pueden incluir URIs para otros recursos, formularios, acciones disponibles y más.

2. **Desacoplamiento del Cliente y el Servidor**: Los clientes no necesitan conocer la estructura exacta del servidor o las rutas de los recursos. En lugar de eso, confían en los enlaces proporcionados por el servidor para navegar por la API.

3. **Auto-descubrimiento**: Los clientes pueden descubrir nuevas funcionalidades y recursos a medida que navegan por la API sin necesidad de documentación externa. Los enlaces y las relaciones proporcionadas en las respuestas guían al cliente.
