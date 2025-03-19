### OpenAPI Descripcion

Estas estructuras se pueden crear en dos tipos de archivos openapi.json o openapi.yaml.

JSON

```json
{
  "anObject": {
    "aNumber": 42,
    "aString": "This is a string",
    "aBoolean": true,
    "nothing": null,
    "arrayOfNumbers": [
      1,
      2,
      3
    ]
  }
}
```

YAML

```yaml
# Anything after a hash sign is a comment
anObject:
  aNumber: 42
  aString: This is a string
  aBoolean: true
  nothing: null
  arrayOfNumbers:
    - 1
    - 2
    - 3
```

### Comparación entre JSON y YAML

**JSON** y **YAML** son dos formatos ampliamente utilizados para representar datos, pero tienen diferencias clave en su sintaxis y características:

1. **JSON**:
   
   - **No soporta comentarios**. No puedes agregar comentarios dentro de un archivo JSON.
   - **Sintaxis estricta**:
     - Se requieren **comas** para separar los campos.
     - Los **objetos** deben estar entre **llaves** (`{}`).
     - Las **cadenas** deben ir entre **comillas dobles** (`"`).
     - Los **arreglos** deben ir entre **corchetes** (`[]`).

2. **YAML**:
   
   - **Permite comentarios**. Puedes agregar comentarios dentro de un archivo YAML utilizando el símbolo `#`.
   - **Sintaxis más flexible**:
     - Se usan **guiones** (`-`) para representar elementos dentro de **arreglos**.
     - La **identación** es muy importante y se utiliza para estructurar los datos, es decir, la jerarquía de los objetos y arreglos depende de la cantidad de espacios en blanco (tabulaciones no están permitidas).
     - La indentación es **obligatoria** en YAML, lo cual puede ser complicado cuando los archivos son muy grandes.

### PROPIEDADES DEL OBJETO PRINCIPAL

1. openapi (obligatorio)

2. info (obligatorio)
   
   Es una descripcion general sobre la API

3. servers (opcional)
   
   Es una lista de URLs base que indican dónde se puede acceder a la API. Cada servidor puede tener una URL y una descripción opcional. Además usar variables para hacer que las URLs sean más dinamicas.

4. path (obligatorio)
   
   Componente importante, ya que define los endpoints, de tu API y las operaciones (metodos HTTP, get, post, put, delete, etc) que se pueden realizar en cada uno.

5. components (opcional)
   
   Seccion donde se definen elementos reutilizables como esquemas, parametros, respuestas, ejemplos, cabeceras y mas. Estos elementos pueden ser referenciados en otras partes de la especificacion OpenAPI. lo que ayuda a evitar la duplicación de código y a mantener la especificacion organizada.

6. security (opcional)
   
   Especifica que esquemas de seguridad deben usarse para acceder a la API. puede
   
   incluir uno o más esquemas de seguridad, y cada esquema puede requerir uno o más socpes (permisos) en el caso de OAuth2

7. tags (opcional)

8. externalDocs (opcional)



:fire: Estructura completa

```json
{ # Objeto JSON
    "openapi": 3.1.0, # Version de OEA utilizada
    "info": { # Objeto JSON
        "title": "string", # Titulo de documentacion API
        "version": 1.0.0, # Version de nuestra documentacion
        "description": "string", # Descripcion de que va nuestra API
        # url que lleva a los terminos de servicio de la API
        # o el servicio que ofrece la API
        "termsOfService": "url",
        # contact, un objeto con la informacion de contacto
        # de los desarrollador/es o soporte de la API
        "contact": {
            "name": "string", # Nombre de equipo de desarrollo
            "url": "url", # Pagina web del equipo
            "email": "correo" # Correo del equipo
        },
        # license, objeto que contiene toda la informacion sobre
        # la licencia de la API (como el nombre de la licencia
        # y su URL)
        "license": {
            "name": "tipo_licencia", # Tipo de licencia
            "url": "url" # url de la licencia
        },
    },
    "servers": [
        {
            # obligatorio
            "url": "url", # url base
            }
        },
        {
            # el nombre de la variable en la url puede ir
            # en la parque que la necesitemos
            "url": "https://{nom_variable}.com/v1"
            # Cambiar de acuerdo a nuestra necesidad
            # la descripcion, este parametro es
            # opcional
            "description": "Servidor de produccion",
            # Define variables que pueden ser usadas en la url
            # tipo objeto
            "variables": {
                "nom_variable": {
                    # valor por defecto (obligatorio)
                    "default": "valor",
                    # Lista de valores permitidos para la variable
                    # obligatorio
                    "enum": ["valor1", "valor2"],
                    # Descripcion de la variable (opcioal)
                    "description": "descripcion_variable"
                }
            # Agregar mas url y description si lo requerimos
            # Como servidor de pruebas u otros
        }
    ],
    "paths": {
        # las claves son las rutas (/users, /products)
        # se pueden definir los parametros que se pueden enviar
        # en la solicitud (paamentros de consulta, parametros de ruta,
        # cabeceras). que se especificar en el objeo parameters y
        # en la url (/users/{userId})
        "/ejemplo/{userID}": {
            # Definimos las operaciones disponibles en la ruta
            # get, post, put, delete, patch, options, head, etc.
            "get": {
                # Es una descripcion breve de lo que hace la
                # operacion ej(Obtener usuario por ID).
                "sumary": "descripcion",
                # Aca agregamos las propiedades del parametro
                # este es un array de objetos json
                "parameters": [
                    # nombre del parametro
                    "name": "userID",
                    # Dónde se envia el parametro
                    # path, query, header, cookie
                    "in": "path",
                    # Indica si el parametro es obligatorio
                    # true o false
                    "required": boolean,
                    # Define el tipo de dato del parametro
                    "schema": {
                        # tipo de dato del parametro
                        # integer, string
                        "type": "tipo_dato"
                    }
                ]
            },
        },
        "/ejemplo": {
            # requesBody -> se especifica solo en los metodos
            # POST, PUT Y PATH, es el cuerpo del body.
            "post": {
                "sumary": "Crear un nuevo usuario",
                "description": "Crea un nuevo usuario en el si",
                "requestBody": {
                    # descripcion del cuerpo
                    "description": "Datos del usuario a crear",
                    # Indca si el cuerpo de la solicitud es
                    obligatorio (opcional), defecto false.
                    "required": true,
                    # Define los formatos de medios (MIME types)
                    # y la estructura de los datos que se
                    # pueden enviar en el cuerpo de la solicitud
                    "content": {
                        # dentro de content, cada tipo de medio
                        # por ejemplo, application/json, puede
                        # tener las siguientes propiedades:
                        "application/json": {
                            # define la estructura de los datos que
                            # se esperan en el cuerpo de solicitud.
                            "schema": {
                                "type": "object",
                                "properties": {
                                    "name": {
                                        "type": "string"
                                    },
                                    "edad": {
                                        "type": "integer"
                                    }
                                }
                            },
                            # Proporciona un ejemplo de cómo deberian
                            # verse los datos, tambien podemos
                            # utilizar la propiedad examples
                            # donde podemos declarar mas de un
                            # ejemplo.
                            "example": {
                                "name": "Jefferson",
                                "age": 25
                            }
                        }
                    }
                }
            }
        }
    },
    "components": {
        # Define los modelos de datos (esquemas) que se
        # utilizan en la API
        "schemas": {
            "User": {
                "type": "object",
                "properties": {
                    "id": {
                        "type": "integer"
                    },
                    "name": {
                        "type": "string"
                    }
                }
            }
        }
    }
}
```



```json
"$ref": "#/components/schemas/User" -> es una referencia al esquema
User definido en components/schemas

# Se puede utlizar en:
"responses": {
  "200": {
    "$ref": "#/components/responses/Success"
  }
}

"parameters": [
  {
    "$ref": "#/components/parameters/userId"
  }
]

"examples": {
  "userExample": {
    "$ref": "#/components/examples/UserExample"
  }
}

"requestBody": {
  "$ref": "#/components/requestBodies/UserRequest"
}
```
