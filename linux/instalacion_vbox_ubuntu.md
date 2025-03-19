# INSTALACION DE VIRTUALBOX

Documentacion de [virtual_box](https://www.virtualbox.org/wiki/Linux_Downloads)

1. Agregar el repositorio
   **Línea de repositorio**:
   Debes agregar una línea a tu archivo `/etc/apt/sources.list`, que le indica a **APT** (el gestor de paquetes de Debian/Ubuntu) de dónde obtener los paquetes de VirtualBox.
   
   ```python
   '''
       Este es el comando proporcionado por la 
       documentacion de vbox.
   
       Remplazar <mydist> por el nombre de la distribución que
       tenemos instalada
   
       Para obtener este nombre utilizamos el comando
       > lsb_release -a
   
       En donde Codename: nombre -> sera el nombre de la distro
   '''
   deb [arch=amd64 signed-by=/usr/share/keyrings/oracle-virtualbox-2016.gpg] https://download.virtualbox.org/virtualbox/debian <mydist> contrib
   ```
   
   :warning: Esta linea se debe agregar al archivo y no ejecutar desde la terminal. Si tenemos una version de ubuntu mas reciente lo que podemos hacer es guardar ejecutar el siguiente comando `sudo nano /etc/apt/sources.list.d/virtualbox.list` y dentro de este agregar la linea anterior "deb..." creada y guardar.

2. Agregar clave publica de oracle
   
   Ejecutamos el siguiente comando en la terminal:
   
   ```python
   # Este es un comando combinado pues descarga y registra
   wget -O- https://www.virtualbox.org/download/oracle_vbox_2016.asc | sudo gpg --yes --output /usr/share/keyrings/oracle-virtualbox-2016.gpg --dearmor
   ```
   
   * Validamos que la clave de oracle se haya guardado correctamente
     
     ```python
     ls /usr/share/keyrings/oracle-virtualbox-2016.gpg
     ```
   
   . Si vemos el archivo significa que la clave se guardo correctamente

3. Actualizamos los repositorios
   
   `sudo apt-get update`

4. Elejimos la version a instalar
   
   `sudo apt-get install virtualbox-7.1` Si requerimos de una distinta es solo cambiar el 7.1 por otra version

5. Posibles problemas con firmas (BADSIG)
   
   Si al intentar actualizar los paquetes desde el repositorio, encontramos este error BADSIG indicando problemas con las firmas de los paquetes, sigue estos pasos para solucionar el problema:
   
   ```python
   ''' 
       Estos comandos eliminan los archivos de lista de 
       paquetes corruptos y actualizan de nuevo.
   '''
   sudo -s -H
   apt-get clean
   rm /var/lib/apt/lists/*
   rm /var/lib/apt/lists/partial/*
   apt-get clean
   apt-get update
   ```
