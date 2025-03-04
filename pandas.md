# PANDAS

Pandas es una **herramienta** (librería) de Python que sirve para trabajar con datos de manera fácil y rápida.

Imagina que tienes una hoja de cálculo de Excel con muchas filas y columnas. Pandas te permite hacer lo mismo en Python: organizar, modificar, analizar y guardar datos.

Documentacion [pandas]([pandas documentation — pandas 2.2.3 documentation](https://pandas.pydata.org/docs/)).

:fire: Intstalación [giuia]([Installation — pandas 2.2.3 documentation](https://pandas.pydata.org/docs/getting_started/install.html))

Se recomienda instalar y ejecutar pandas desde un entorno virtual, por ejemplo, usando el venv o virtualenv.

1. Instalación de libreria pandas
   
   ```python
   pip install pandas
   ```

2. Instalar depencias requeridas
   
   * [numpy]([NumPy - Installing NumPy](https://numpy.org/install/))
   
   * [dateutil]([dateutil - powerful extensions to datetime — dateutil 3.9.0 documentation](https://dateutil.readthedocs.io/en/stable/))
   
   * [pytz]([pytz · PyPI](https://pypi.org/project/pytz/))
   
   * [tzdata]([tzdata · PyPI](https://pypi.org/project/tzdata/2025.1/#description))
   
   ```python
   pip install numpy # numpy
   pip install python-dateutil #dateutil
   pip install pytz #pytz
   pip install tzdata==2025.1 #tzdata
   ```

3. Instalar [dependencias]([Installation — pandas 2.2.3 documentation](https://pandas.pydata.org/docs/getting_started/install.html#install-optional-dependencies)) opcionales
   
   ```python
   pip install[dependencia]
   # instalar las recomendadas, opcional
   pip install "pandas[performance]"
   # visualizacion en formato tabular, opcional
   pip install "pandas[plot, output-formatting]"
   # para trabajar con archivos excel
   pip install "pandas[excel]"
   ```
   
   Documentacion [tabulate]([astanin/python-tabulate: Datos tabulares de impresión bonita en Python, una biblioteca y una utilidad de línea de comandos. Repositorio migrado desde bitbucket.org/astanin/python-tabulate.](https://github.com/astanin/python-tabulate))


