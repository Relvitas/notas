## PYENV

`pyenv` es una herramienta que permite **gestionar múltiples versiones de Python** en un mismo sistema. Es útil cuando necesitas trabajar con diferentes versiones de Python en distintos proyectos sin afectar la instalación global de Python en tu sistema.

:penguin:  Guia de instalacion para linux/ubuntu

1. Instalar dependencias
   
   Estas son requeridas para la instalacion de diferentes versiones de python con pyenv
   
   ```bash
   sudo apt update; sudo apt install build-essential libssl-dev zlib1g-dev \
   libbz2-dev libreadline-dev libsqlite3-dev curl git \
   libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
   ```

2. Validar si curl esta instalado
   
   * Ejecutar `curl -V` Si obtenemos algun resultado, este esta instalado.
     
     De lo contrario instalarlo mediante `sudo apt install curl -y`

3. Instalar pyenv
   
   `curl https://pyenv.run | bash` una vez termine la instalacion este nos mostrara un WARNING con unas rutas que se deben agregar al archivo .bashrc
   
   ```bash
   # Abrir el archvo .bashrc
   vi ~/.bashrc
   
   # Pegar al final del archivo, las rutas mostradas
   
   # CONFIGURACION DE PYENV
   export PYENV_ROOT="$HOME/.pyenv"
   [[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"
   eval "$(pyenv init - bash)"
   
   # Al finalizar se debe reiniciar la terminal
   exec "$SHELL"
   ```

4. En caso de algun error
   
   Instalar los [pre-requisitos]([Common build problems · pyenv/pyenv Wiki · GitHub](https://github.com/pyenv/pyenv/wiki/Common-build-problems#prerequisites))

5. Validar si se instalo correctamente
   
   `pyenv --version` Si este se instala mostrara su version

:penguin: Uso pyenv

* Listar versiones de python disponibles para su instalacion
  
  `pyenv install --list`

* Instalar una version de python
  
  `pyenv install <version>`

* Listar versiones instaladas en el sistema
  
  `pyenv versions`
  El `*` indica la versión actualmente activada.

* Cambiar version de python globalmente
  
  `pyenv global <version>`

* Usar una version solo en una carpeta (proyecto especifico)
  
  Si estás trabajando en un proyecto y quieres usar una versión específica de Python:
  
  ```python
  cd /ruta/tu-proyecto # Ingresar a la carpeta del proyecto
  pyenv local <version> # Indicar version de python´ 
  '''
      Esto crea un archivo .python-version dentro 
      del proyecto, y cada vez que entres en esa carpeta, 
      pyenv usará automáticamente esa versión de Python.
  '''
  ```

* Actualizar pyenv
  
  `pyenv update`

* Desinstalar versiones de python
  
  `pyenv uninstall <version>`

:penguin: Otras opciones

* Desintalar pyenv
  
  ```bash
  # Ejecutar el comando
  rm -fr ~/.pyenv
  
  # Eliminar las rutas agregadas al archibo .bashrc
  
  # Reiniciar la shell
  exec "$SHELL"
  ```

* Manual de comandos
  
  [pyenv_command](https://github.com/pyenv/pyenv/blob/master/COMMANDS.md)

---

## PYENV VIRTUALENV

pyenv-virtualenv es un plugin de pyenv que proporciona características para gestionar entornos virtuales y conda para Python en sistemas similares a UNIX.

:penguin: Instalación de plugin para linux/ubuntu

1. Clonar repositorio de pyenv-virtualenv dentro de pyenv
   
   ```bash
   '''
       $(pyenv root)
       Variable que apunta a la ubicacion donde pyenv
       esta instalado.
   
       Si la ruta de instalacion del pyenv es personalizada
       cambiar $(pyenv root) por la ruta donde se encuentra este
       eje: /opt/pyenv/plugins/pyenv-virtualenv
   '''
   
   # Conocer la ruta donde esta instlado pyenv
   pyenv root
   
   git clone https://github.com/pyenv/pyenv-virtualenv.git $(pyenv root)/plugins/pyenv-virtualenv
   
   '''
       Si tenemos el error (already exist)
       Validar si ya tenemos instalado pyenv-virtualenv.
   
       Si el comando no regresa nada, significa que no esta
       activida en la shell, si muestra algo relacionado, entonces
       el plugin esta instalado correctamente.
   '''
   pyenv help | grep virtualenv
   ```
   
   2. (Opcional) Activar la activacion automatica de env
      
      ```bash
      # Ejecutar el comando
      vi ~/.bashrc
      
      # Agregar al archivo .bashrc
      # CONFIGURACION DE VIRTUALENV
      eval "$(pyenv virtualenv-init -)"
      
      '''
          Si la ruta de instalacion de pyenv es personalizada
          por favor cambiar el comando.
      '''
      eval "$(ruta/pyenv virtualenv-init -)"
      
      # Aplicar cambios 
      source ~/.bashrc
      # Reiniciar shell
      exec "$SHELL"
      ```

:penguin: Uso pyenv-virtualenv

* Crear un virtualenv
  
  Para crear un virtualenv para la versión Python utilizado con pyenv, ejecute pyenv virtualenv, especificando la versión de Python que desea y el nombre del directorio virtualenv. Por ejemplo,
  
  ```python
  '''
      pyenv virtualenv <versión-python> <nombre-del-entorno>
  '''
  pyenv virtualenv 2.7.10 my-virtual-env-2.7.10
  ```

* Ver entornos creados
  
  `pyenv virtualenvs`

* Activar un entorno
  
  `pyenv activate mi-entorno`

* Desactivar un entorno
  
  `pyenv deactivate`

* Eliminar un entorno virtual
  
  `pyenv virtualenv-delete mi-entorno`

---

## INSTALAR LIBRERIA VIRTUALENV

1. Instalar [pipx](https://pipx.pypa.io/stable/)
   
   Pipx es una herramienta para ayudarle a instalar y ejecutar
   aplicaciones de usuario final escritas en Python. Es más o menos similar
   a la de macOS. `brew`, [Npx](https://medium.com/@maybekatz/introducing-npx-an-npm-package-runner-55f7d4bd282b) de JavaScript, y Linux `apt`.
   
   Está estrechamente relacionado con el pip. De hecho, utiliza pip,
   pero se centra en la instalación y gestión de paquetes Python que pueden
   correr desde la línea de comandos directamente como aplicaciones.
   
   ```bash
   sudo apt update
   sudo apt install pipx
   pipx ensurepath
   ```

2. Instalar virtualenv
   
   `virtualenv`es una herramienta para crear entornos Python aislados. Desde Python `3.3`, un subconjunto de ella ha sido integrado en la biblioteca estándar bajo el [módulo de venv](https://docs.python.org/3/library/venv.html). El `venv`el módulo no ofrece todas las características de esta biblioteca, por nombrar sólo algunas más prominentes:
   
   - es más lento (por no tener el `app-data`método de semillas).
   - no es tan extensible.
   - no puede crear entornos virtuales para versiones de pitón instalada arbitrariamente (y descubrirlas automáticamente).
   - no es actualizable vía [pip](https://pip.pypa.io/en/stable/installing/).
   - no tiene una API programática tan rica (describir entornos virtuales sin crearlos).
   3. Crear entorno virtual
      
      ```bash
      mkdir nom_proyecto -> nombre de carpeta almacenadora del proyecto
      virtualenv env_name -> Crea el entorno "crea una carpeta en el directorio actual"
      .\env_name\Scripts\activate -> activa el entorno en windows
      source env_name/bin/activate -> en linux
      ```

---

## VENV

Herramienta estándar de Python (desde Python 3.3)

1. Crear un entorno virtual
   
   `python -m venv mi_env`
   Esto crea una carpeta llamada `mi_env`, que contiene una versión aislada de Python y pip.

2. Activar entorno virtual
   
   `source mi_env/bin/activate`

3. Salir del entorno virtual
   
   `deactivate`

4. Eliminar un entorno virtual
   
   ```bash
   rm -rf mi_env  # En Linux/macOS
   rmdir /s /q mi_env  # En Windows
   ```
