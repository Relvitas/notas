# FLET

:pushpin: **INSTALACION**

* `pip install 'flet[all]'` | de esta forma instalamos Flet. 

:pushpin: **COMANDOS**

* `fler create` | se encarga de crear la estructura de un proyecto

* `flet run <ruta>` | ejecuta la aplicación, podemos solo ejecutar flet run sin el argumento la y se ejecutara el main en donde estemos ubicados.

* `flet run --web <ruta>` | ejecuta el app en la web también podemos cambiar este `--web` por `-w`

* `flet run -r` | flet se queda vigilando los archivos, cuando guardamos un cambio, la aplicación se actualiza automáticamente sin cerrarse.

* `flet run -d` | le dice a flet que busque el archivo principal en un directorio especifico o que use el modo de desarrollo más profundo.
  * Nota técnica: Normalmente, si solo hacemos flet run, este busca un archivo llamado `main.py`. si nuestra estructura es distinta, el flag `-d` ayuda a especificar la ruta.

:pushpin: **METODOS**

* `page.add(segmento, segmento2)` | permite agregar objetos a ventana.
* `ft.button("valor")` | crea un botón. 
