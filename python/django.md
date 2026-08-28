# DJANGO

Es un framework de desarrollo web de alto nivel para Python.

## INSTALACION DJANGO

Versiones disponibles y como instalar: [URL](https://www.djangoproject.com/download/)

* *Global:* Linux `python -m pip install Django==version`
* *Por proyecto:* Linux. Este se ejecuta dentro de un entorno virtual `python -m pip install Django==version`

### COMPROBAR VERSION INSTALADA

```python
# Dentro de python
>>> import django
>>> print(django.get_version()) # retorna la version

# Comando
python -m django --version
```

## COMANDOS

* Herramientas Django: `django-admin`, este comando nos muestra una lista de funciones que posee el comando.
* Iniciar proyecto
  * Carpeta actual:
  `django-admin startproject config .`, crea el proyecto en donde el paquete de se renombra como config.
  * Carpeta nueva:
  `django-admin startproject [nombre_proyecto]`, de esta forma el paquete de configuración toma el nombre que le dimos al proyecto.
* Iniciar servidor de desarrollo: `python manage.py runserver`
* Crear una app: `python manage.py startapp [nombre_aplicacion]` Importante entender que una aplicación es una funcionalidad, podemos verlos como paquetes y el nombre va en singular.

## ARCHIVOS DE CONFIGURATION

* `manage.py:` Este es como el control remoto del proyecto. En este archivo le damos ordenes a Django.
* `mysite/ | config/` Este es el cerebro del proyecto, este nombre se utiliza para importar cosas.
* `mysite/__init__.py:` Es un archivo vació, su misión es indicar que la carpeta es un paquete de python.
* `mysite/settings.py:`Este es el archivo de configuración. Contiene cosas como la base de datos, rutas, apps instaladas.
* `mysite/urls.py:` Este es el archivo de rutas y vistas
* `mysite/asgi.py:` Es la entrada para servidores modernos. Django puede hacer varias cosas al mismo tiempo.
* `mysite/wsgi.py:` Es la entrada para servidores tradicionales.

## ARCHIVOS DE UNA APP

* `manage.py:` Aquí defines la estructura de datos (tablas de la base de datos).
* `views.py:` Contiene la lógica que responde peticiones HTTP. Las vistas reciben requests y devuelven responses.
* `admin.py:` Sirve para registrar modelos en el panel admin de Django.
* `apps.py:` Configuración de la app. Django usa esto internamente para reconocer la app. Normalmente casi nunca lo tocas al inicio.
* `test.py:` Para pruebas automáticas. Aquí escribes tests para validar que todo funciona.
* `migrations/:` Carpeta donde Django guarda cambios de la base de datos.
* `urls.py:` Django NO lo crea automáticamente en la app, pero casi siempre deberías crear uno. Sirve para las rutas de la app.
* `templates/:` HTML de la app.
* `static/:` CSS, JS, imágenes.

## EXTENSIONES

* [Django](https://marketplace.visualstudio.com/items?itemName=batisteo.vscode-django)
* [Django Snippets](https://marketplace.visualstudio.com/items?itemName=bibhasdn.django-snippets)
* [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python)
* [Pylance](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance)
* [Python Debugger](https://marketplace.visualstudio.com/items?itemName=ms-python.debugpy)
* [Autopep8](https://marketplace.visualstudio.com/items?itemName=ms-python.autopep8)
* [Python Indent](https://marketplace.visualstudio.com/items?itemName=KevinRose.vsc-python-indent)

## URLs y Views

Cuando alguien entra a una pagina web `misitio.com/hola` Django tiene que preguntarse 🤔 “¿Quién debe responder esta dirección?” es hay cuando entra en juego:

urls.py → el mapa 🗺️
views.py → las personas que responden 📞

```python
mi_proyecto/
│
├── mi_proyecto/
│   ├── settings.py
│   ├── urls.py   ← URLS DEL PROYECTO
│
├── juegos/
│   ├── views.py
│   ├── urls.py   ← URLS DEL APP
```

:pushpin: 1. urls.py DEL PROYECTO
Este es el jefe principal 👑.
Se encarga de decir:

👉 “Si alguien entra a `/juegos/`, envíalo al app juegos”.

Ejemplo:
```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    # Todas las rutas que empiecen con juegos/
    # serán manejadas por el archivo juegos/urls.py”
    path('juegos/', include('juegos.urls')),
]
```

:pushpin: 2. urls.py DEL APP

Ahora el app recibe el trabajo 📬.
Este archivo decide:
👉 “¿Qué view debe responder?”

Ejemplo:
```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.inicio),
    path('pokemon/', views.pokemon),
]
```

El `''` significa:
👉 “la ruta vacía”
Entonces: `/juegos/`
usa: `views.inicio`

:pushpin: 3. views.py
Aquí vive la lógica 🧠.
Las views son funciones que responden al usuario.

Ejemplo:
```python
from django.http import HttpResponse

def inicio(request):
    return HttpResponse("Página principal")
s
def pokemon(request):
    return HttpResponse("Página Pokémon")
```

## Instalar apache y mod_wsgi

Importante es para un (despliegue en producción), si solo es para pruebas utilizar la intalacion del serivdor libiano.

1. Descargar [apache]([Download - The Apache HTTP Server Project](https://httpd.apache.org/download.cgi)):
   
   ```python
   '''
       Dirigirse a la ruta proporcionada, y ubicar la linea
       * 'Apache HTTP Server <version> (httpd): <version> is the 
           latest available version'
   
       * Dar click en source: httpd-<version>.tar.gz
   '''
   ```

2. Extraer el archivo
   
   ```python
   $ gzip -d httpd-NN.tar.gz
   $ tar xvf httpd-NN.tar
   ```

3. Verificar si tenemos intalado gcc
   
   ```python
   gcc --version
   '''
       Si gcc esta instalado veremos algo como lo siguiente:
   '''
   gcc (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0
   Copyright (C) 2021 Free Software Foundation, Inc.
   
   # De lo contrario tendremos:
   Command 'gcc' not found, but can be installed with:
   sudo apt install gcc
   
   # Instalar update
   sudo apt update
   sudo apt install build-essential
   # Instalar make
   sudo apt install make
   # Agregar al path
   export PATH=/usr/bin:$PATH
   ```

4. Instalacion de PCRE2
   
   ```python
   '''
       Descargar pcre2, validar si estamos con la ultima
           version de pcre2 es decir cambiar <version> por
           la version
           http://github.com/PCRE2Project/pcre2/releases
   '''
   wget https://github.com/PCRE2Project/pcre2/releases/download/pcre2-<version>/pcre2-<version>.tar.gz
   tar -xvzf pcre2-<version>.tar.gz # Extraer
   cd pcre2-<version> # Acceder a la carpeta
   
   # Configurar y compilar
   ./configure --prefix=/usr/local/pcre2
   make
   sudo make install
   
   # Agregar las variables de entorno
   export PATH=/usr/local/pcre2/bin:$PATH
   
   # Verificar la ubicacion
   # Si no muestra ninguna ruta, no esta en nuestra path
   which pcre2-config
   
   # Validar si se instalo correctamente
   pcre2-config --version
   ```

5. Ubicarse en la carpeta extraida y crear la siguientes carpertas
   
   ```python
   cd http-<version>
   
   '''
       * Validar si existe una carpeta "srclib"
           si esta no existe se debe crear.
   '''
   mkdir -p srclib
   
   '''
       * Se deben crear las siguientes 2 carpertas
           dentro del directorio srclib
   '''
   mkdir ./apr ./apr-util
   ```

6. Descargar [APR]([Download - The Apache Portable Runtime Project](https://apr.apache.org/download.cgi)) (apache portable runtime) y APR-Util
   
   ```python
   '''
       * Extraer cada uno de estos en las rutas 
           creadas en el paso anterior
   '''
   tar -xvzf apr-1.7.x.tar.gz --strip-components=1 -C path/srclib/apr
   tar -xvzf apr-util-1.6.x.tar.gz --strip-components=1 -C path/srclib/apr-util
   
   '''
       Configurar el codigo fuente de apache
       * El parámetro --with-include-apr le dice a apache
           que use las versiones de APR y APR-Util que colomos
           en srclib
       * Este comando se ejecuta dentro de la carpeta extraida
   '''
   cd 
   # COnfigrua apache para usar apr y apr-util
   ./configure --with-included-apr
   make -j$(nproc)
   
   # Debemos indicar la version pcre a usar
   ./configure --prefix=/usr/local/apache2 --with-pcre=/usr/local/pcre2/bin/pcre2-config
   
   # Compilar apache e instalar
   make
   
   # Posible error
   '''
       indica que el compilador no puede encontrar el 
       archivo de cabecera expat.h, que es necesario para 
       compilar el módulo apr_xml de APR-Util. 
       Este archivo pertenece a la librería Expat, 
       que es una librería para analizar XML.
   '''
   xml/apr_xml.c:35:10: fatal error: expat.h: No such file or directory
      35 | #include <expat.h>
         |          ^~~~~~~~~
   compilation terminated.
   # Solucion
   make clean
   sudo apt update
   sudo apt install libexpat1-dev
   ./configure --with-expat=builtin
   make
   sudo make installmake
   # Verificar instalacion
   find /usr -name "expat.h"
   ```

7. Agregar al patch
   
   ```python
   # Revisar si el ejecutable se encuentra de la ruta
   # si vemos archivos httpd o apachectl
   # todo esta correcto
   ls -l /usr/local/apache2/bin/
   
   # Si todo esta OK
   ## Agregar al path
   echo 'export PATH=/usr/local/apache2/bin:$PATH' >> ~/.bashrc
   source ~/.bashrc
   
   ## Validar si agrego correctamente al PATH
   httpd -v
   apachectl -v
   
   # Crear servicion acpache
   sudo nano /etc/systemd/system/httpd.service
   # Agregar el siguiente contenido
   # Guarda el archivo con CTRL + X, luego Y y ENTER.
   [Unit]
   Description=Apache HTTP Server
   After=network.target
   
   [Service]
   ExecStart=/usr/local/apache2/bin/httpd -k start
   ExecReload=/usr/local/apache2/bin/httpd -k restart
   ExecStop=/usr/local/apache2/bin/httpd -k stop
   PIDFile=/usr/local/apache2/logs/httpd.pid
   Type=forking
   
   [Install]
   WantedBy=multi-user.target
   
   # Recargar para aplicar cambios
   sudo systemctl daemon-reload
   sudo systemctl start httpd # Iniciar servidor
   sudo systemctl status httpd # Verificar el estado
   sudo systemctl stop httpd # Detener el servicio
   sudo systemctl restart httpd # Reiniciar servidor
   ```

8. Sincronizar el reloj del sistema
   
   Esto es importante para garantizar que tu servidor tenga la hora exacta, lo cual es crucial para aplicaciones como **Apache HTTP Server**, donde los elementos del protocolo HTTP (como las cabeceras de fecha y hora) dependen de un reloj preciso.
   
   ```python
   # Instalar chrony
   sudo apt install chrony
   
   # Configurar chrony
   sudo nano /etc/chrony/chrony.conf
   # Agregar o descomentar las lineas con servidores NTP
   server 0.pool.ntp.org iburst
   server 1.pool.ntp.org iburst
   server 2.pool.ntp.org iburst
   server 3.pool.ntp.org iburst
   
   # Iniciar y habilitar el servicio
   sudo systemctl restart chronyd
   sudo systemctl enable chrony
   
   # Verificar el estado del servicio
   sudo systemctl status chrony
   
   # Ver que servidores esta utilizando
   chronyc sources -v
   
   # Verificar la sincronización
   # Se visualiza con que servidores de tiempo se esta
   # sincronizando chrony
   chronyc tracking
   
   # Si todo esta bien nuestro servidor tiene la hora correcta
   timedatectl 
   '''
   ^* alphyn.canonical.com → Este es el servidor que chrony considera el mejor (indicado por *).
   ^+ prod-ntp-3.ntp4.ps5.cano> → Estos servidores (+) están siendo usados para ajustar la hora, pero no son la fuente principal.
   ^- co.ntp.nu → Este servidor (-) no está siendo utilizado en la combinación porque no es tan confiable como los otros.
   Stratum → Indica la jerarquía del servidor NTP (cuanto más bajo, mejor; 1 es una fuente directa).
   LastRx → Indica cuántos segundos han pasado desde la última respuesta.
   Last sample → Muestra el desfase de tiempo con respecto a tu sistema.
   '''
   ```

```
9. **mod_wsgi-express**

Es una herramienta para ejecutar aplicaciones Python WSGI (como Django o Flask) usando Apache y mod_wsgi de manera sencilla.

Para que sirve:

* Proporciona una forma rápida de probar aplicaciones WSGI sin configurar Apache manual mente.

* Facilita el despliegue local sin modificar archivos de configuracion complejo

:fire: Instalacion

Recuerda ejecutar este dentro de un virtual

`pip install mod_wsgi`

* Iniciar el servidor con una app WSGI

  Si tenemos un archivo app.py con una aplicacion WSGI, podemos ejecutarlo asi:

  `mod_wsgi-express start-server app.py`

  Esto inicia un servidor con Apache y mod_wsgi, listo para probar la app

* Especificar un puerto

  Por defecto usa el puerto 8000, pero podemos cambiarlo

  `mod_wsgi-express start-server app.py --port 8080`

* Ver logs en tiempo real

  Si necesitamos depurar

  `mod_wsgi-express start-server app.py --log-to-terminal`

* Generar configuracion para apache

  Esto imprime la configuracion que podemos agregar al archivo de configracion de apache, por si deseamos integrar la aplicacion con el servidor de apache.

  `mod_wsgi-express module-config`

* Validar si esta correctamente instalado

  `mod_wsgi-express version`
```

MTV

Template/vista

model/model

view/controller

---

:fire: **Crear un proyecto**

1. `mkdir <nombre_proyecto>` Este comando creara la carpeta que contendra nuestro proyecto.

2. `django-amdin startproject <nombre_proyecto> <nombre_carpeta_proyecto>` Este comando crea el proyecto dentro de la carpeta creada en el paso anterior.

:fire: Construir nuevos cambios

`python manage.py makemigrations`

:fire: `python manage.py runserver` 

Este comando ejecuta el servidor de desarrollo integrado para pruebas.

1. `python manage.py migrate` Este comando lo debemos ejecutar si tenemos algun error con migraciones pendientes, No olvidemos primero detener el servidor y proceder con la ejecucion del comando.

:fire: `python manage.py startapp <nom_modulo>` 

Este comando sirve para crear un modulo de la pagina web.

---

## CREAR VISTAS

```python
'''
    1. En el modulo de la app generado, tenemos un archivo
        de nombre views este lo podemos ver como el controlador
        en donde gestionaresmos las vistas, se definen funciones
        que llevaran el nombre de la vista.

        importante en la seccion views agregar la clase
        HttpResponse.

        from django.http import HttpRespose

        def inicio(request):
            return HttpRespose(contenido_retorno)

    2. Una ves creada la vista debemos asignar esta vista a una
        URL, es decir cuando el usuario busque cierta url se
        cargara lo que este asociado en la funcion de la vista
        podemos ver esto como un indexer.

        from django.urls import path
        from . import views # Acá importamos todas las vistas,
                            # el . señala que esta en la
                            # carpeta actual.

        urlpatterns = [
            path("nombre_path/", views.nom_vista, name="nombre_url")
        ]

        # nombre_path -> Sera el indentificativo cuando el usuario
                realice la buqueda a la vista, es decir inicio/
                cuando el usuario haga la busqueda asi:
                pagina: .com/inicio lo llevara a la vista
                relacionada.

        # views.nom_vista -> el nom_vista sera el nombre
            que establecimos en la funcion que contiene la
            vista en views

        # nombre_url -> sera el nombre que identifica la URL.

    3. Agregaremos las urls de la app al proyecto, esto
        lo aremos en donde se creo el primer proyecto en el
        modulo urls.py debemos importar el include.

        from django.urls import path, include

        urlpatterns = [
            path('', include("modulo.urls")),
        ]

        # modulo.urls -> este señala al modulo de la app urls
            ejemplo: app.urls

        # '' -> sera el identificador de la url inicial, este
            puede cambiar si tenemos mas apps. ejemplo
            blos/ la url seria .com/blog pero con la inical
            seria .com
'''
```

## PASAR PARAMETROS A UNA VISTA

```python
'''
    1. configuracion controlador/view del app
'''
def nom_vista(request, param):
    # operaciones con la variable param

'''
    2. configuracion de la urls del app.

    Si necesitamos convertir los datos a enteros utilizamos
    <int:param> # convierte a entero

    urlpatterns = [
        path('user/<int:id>/', views.nom_vista, name="nom_url")
    ]

    # Si necesitamos pasar mas de un parametro esto se hace:
    utrpatterns = [
        path('user/<int:edad>/<int:id>/', views.nom, name="nom"),
    ]

    Y no olvidar agregar esto a las funciones de las vista.
    def nom_vista(request, param1, param2):
        # operaciones con parametros
        return HttpResponse()
'''
```

## PLANTILLAS

Las plantillas son cadenas de texto (HTML casi siempre), siven para separar la parte lógica (dato) de la parte visual (presentacion) de un documento web.

1. Creacion del objeto Template `plt=Template(doc_externo.read())`

2. Creación de contexto `ctx=Context()`
   
   Datos adicionales para el template (variables, funciones etc).

3. Renderizado del objeto template `documento=plt.render(ctx)`

## DATABASE / MODEL (psql)

1. `pip install --upgrade pip` Este comando actualiza pip a su ultima version

2. `pip install "psycopg[binary]"` Instala la biblioteca junto con las dependencias binarias precompiladas para facilitar la instalación sin complicaciones adicionales.

3. Configurar postgresql en django (**settings.py**) este es el archivo se encuenta en la creacion del proyecto con django.
   
   1. Abrir settings.py, buscar la seccion DATABASES y cambiar lo que contiene esta, que por defecto biene configurada para SQLite.
   
   ```python
   DATABASES = {
       'default': {
           'ENGINE': 'django.db.backends.postgresql',
           'NAME': 'nombre_de_tu_base_de_datos',  # El nombre de tu base de datos
           'USER': 'nombre_de_usuario',  # Tu nombre de usuario de PostgreSQL
           'PASSWORD': 'tu_contraseña',  # Tu contraseña de PostgreSQL
           'HOST': 'localhost',  # O la IP del servidor de PostgreSQL si no está en el mismo equipo
           'PORT': '5432',  # Puerto por defecto de PostgreSQL
       }
   }
   ```
   
   Otra forma de configurar esta, es con los archivos de configuracion de apache, seguir la documentacion de [django]([Databases | Django documentation | Django](https://docs.djangoproject.com/en/5.1/ref/databases/#postgresql-notes)).

4. `python manage.py makemigrations` Este comando construye las nuevas migraciones.

5. python manage.py migrate

**GENERAR LAS CONSULTAS DE LA CONSTRUCION DE DB**

Una vez, tengamos el models OK, debemos generar las querys, esto se realiza con el comando, `python manage.py sqlmigrate <nombre_aplicacion> <numero_migracion>` el numero de migracion se obtiene al construir las migraciones de la app ej: `auxiliares\migrations\0001_initial.py` -> 0001 es el numero de migracion.

## MANEJAR ARCHIVOS

1. Configurar `MEDIA_URL` Y `MEDIA_ROOT`
   
   ```python
   '''
       Agregamos estas configuraciones en la raiz del proyecto
       settings.py
   '''
   # Indicamos a dnjango a donde subir archivos y donde guardarlos
   MEDIA_URL = '/media/' # URL publica para acceder a los archivos
   MEDIA_ROOT = os.path.join(BASE_DIR, 'media') # Ruta en el servidor donde se guardan los archivos
   ```
