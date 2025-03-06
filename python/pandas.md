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

---

## GENERAL

* Pandas ofrece dos tipos de clases para el manejo de datos
  
  * `Series`: una matriz de etiquetas unidimencional. Referente a las columnas de una tabla.
  
  * `DataFrame`: Una estructura de datos bidimensional. Referente a filas y columnas.

:fire: Importar pandas

```python
import pandas as pd 
'''
    * pd -> es el alias comúnmente usado para importar la
    libreria.
'''
```

----

## METODOS DATAFRAME

:fire: dropna()

Se utiliza para eliminar las filas o columnas que contienen valores nulos (`NaN`). Esto es muy útil cuando se quiere limpiar un DataFrame de datos faltantes antes de realizar análisis o procesamiento adicional.

```python
'''
Argumentos:
    axis (int): Decide si se eliminan filas (0) o columnas (1)
        El valor predeterminado de este es 0.

    how (str): Determina si se eliminan las filas/columnas:
        'any': Este valor eliminará las filas o columnas 
            que contengan al menos un valor nulo. Es decir, 
            si hay algún NaN en la fila o columna, 
            esta será eliminada.

        'all': Este valor eliminará las filas o columnas 
            solo si todos los valores en la fila o columna 
            son nulos. Es decir, la fila o columna será 
            eliminada si todos sus elementos son NaN.

    thresh (int): Requiere que un número mínimo de 
        valores no nulos esté presente para que 
        la fila/columna no sea eliminada. El valor 
        predeterminado es None.

    subset (list): Especifica las filas/columnas en las que 
        buscar valores nulos. El valor predeterminado es None. 

    inplace (bool): Si es True, modifica el DataFrame 
        original en lugar de devolver una copia. 
        El valor predeterminado es False.
'''
DataFrame.dropna(
    axis=0, 
    how='any', 
    thresh=None, 
    subset=None, 
    inplace=False
)


# Eliminar filas con valores nulos en las columnas 'A' y 'B'
df_limpio = df.dropna(subset=['A', 'B'])
```



:fire: apply()

Se utiliza para aplicar una función a lo largo de un eje de un DataFrame(filas o columnas).

```python
'''
    Argumentos:
        func (func): La función que deseas aplicar, Puede ser una función
            definida por el usuario o una función de libreria.

        axis (int): El eje a lo largo del cual se aplica la función.
            * 0 -> aplica la funcion a lo largo de las filas
            * 1 -> Para aplicar la funcion a lo largo de las columnas

        raw (bool): Si es True, pasa una ndarray en lugar de una Serie
            al aplicar la funcion.

        result_type: Tipo de salida:
                * 'expand' Expande los resultados en un 
                    DataFrame separado (o Serie si se aplica a una Serie).
                * 'reduce' Intenta reducir la dimensión del resultado.
                * 'broadcast' Expande la forma del resultado para igualar la entrada.
                * None (por defecto) La salida es la 
                    forma predeterminada según la función aplicada.

        args y **kwds: Argumentos y palabras clave que se pasan a
            la funcion.
'''
DataFrame.apply(
    func,
    axis=0,
    raw=False,
    result_type=None,
    args=(),
    **kwds
)

def actualizar_fila(row):
    if pd.isna(row['País']):
        row['País'] = 'Desconocido'
    return row
df = df.apply(actualizar_fila, axis=1)
```



---



## CONSTRUCCIONES

:fire: Cortar y pegar un dato de columna A a una column B

```python
def actualizar_fila(column):
    if pd.isna(column['País']): # Busqueda de datos NaN
        column['País'] = column['Nombre'] # Remplazar valor de A por B
        column['Nombre'] = np.nan # Vaciar columna B
    return column # Retornar DataFrame

df = df.apply(actualizar_fila, axis=1)
```

:fire: Eliminar columnas vacias

```python
df = df.dropna(axis=1, how='all')
```
