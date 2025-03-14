# DJANGO

* Verificar que versiones de django es compatible con python

    [FAQ: Installation | Django documentation | Django](https://docs.djangoproject.com/en/5.1/faq/install/#faq-python-version-support)

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
   
   
