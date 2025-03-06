## MANEJO DE ARCHIVOS

```python
'''
    este se utiliza para abrir un archivo o crear uno
    en caso de no existir, se pueden indicar parametros
    para leer informacion del archivo o para escribir
    directamente sobre este.

    rutaArchivo: debemos especificar la ubicación del archivo, 
        tener encuenta que se deben escapar 
        los "\" con "\\"" para que no lo tome como un caractere
        especial c:\\user\\desktop\\archivo.txt
        Si es mac o linux no hay necesidad 
        de escapar estos, dado a que se utiliza
el "/"

    modos:
    * 'w', especifica el modo escritura en el archivo y 
        crea el archivo si este no existe
    * 'r', especifica el modo lectura, este valor esta por default
    * 'a', append -> agregar informacion a un archivo
        sin que la anterior se elimine
    * 'x' create -> crea un arhivo especificado y 
        manda un error en caso de que ya lo este
    * 't' -> para el tipo de archivo texto, modo default
    * 'b' -> binary: modo binario (imagenes)

    Modos combinados:
    * 'w+' -> lo vamos a utilizar para escribir como leer informacion
    * 'r+' -> lo vamos a utilizar para leer informacion como para escribir

    encoding='utf8' -> set de caracteres
'''
nomVar = open('rutaArchivo', 'modo', encoding='utf8')

'''
    agregar texto aun archivo, no se permiten los acentos
    a no ser que los configuremos utf...
'''
nomVar.write('texto')

# cerrar el archivo
nomVar.close()
'''
    leer toda la informacion que contiene el archivo
    tambien podemos especificar la cantidad de caracteres
    que queremos mostrar (5)
'''
nomVar.read()

# Nos permite leer lineas de un archivo                
nomVar.readline()

# se pueden recorrer todas las lineas de un archivo con un ciclo for in
for linea in nomVarDelArchivo:
    print(linea)

'''
    esto regresa una lista, cada linea la toma como
    un dato por se parado, es decir cada linea tendria un indice
'''
nomVar.readlines()

# se puede acceder a una linea especifica dando su indice
readlines()[0]

# CREAR COPIA DEL ARCHIVO
# se crea nuevo archivo y se anexa al final del archivo
nomVarCopia = open('copia.txt', 'a') 
# se pasa lectura del archivo 1
nomVarCopia.write(nomVar.read()) 

nomVarCopia.close()
nomVar.close()
```

:fire: Otra forma de manejo de archivos

con esta forma se cierran los recursos automaticamente
with lo que hace es llamar el metodo **enter** y al finalizar
se llama el metodo **exit** de manera automatica

```python
with open('./ruta/archivo.txt', 'r', encoding="utf8") as nomObjeto:

print(nomObjeto.read())

# CLASE DE CONTROL PARA WITH
class ManejoArchivo:
    def __init__(self, nombreObjeto):
        self._nombreObjeto = nombreObjeto

    def __enter__(self):
        print('Obtenemos el recurso'.center(50,'-'))
        self._nombreObjeto = open('./ruta/archivo.txt', 'modo', encoding="utf8")
        return self._nomObjeto

    def __exit__(self, tipoExcepcion, valorExcepcion, trazaError):
        print('Cerramos recurso'.center(50, '-'))
        if self._nombreObjeto:
            self._nombreObjeto.close()

with ManejoArchivos('nomArchivo.txt') as nomObjeto:
    print(nomObjeto.read())
```

:fire: csv

El módulo `csv` de Python permite leer y escribir archivos en formato CSV (Comma-Separated Values). Aquí tienes una guía sobre su uso:

```python
import csv

whith open('ruta.csv', mode='r') as nombre_contenedor
    '''
        Abrir el archivo csv en modo diccionario 
        y almacenarlo en csv_lectura como un diccionario
    '''
    csv_lectura = csv.DictReader(nombre_contenedor)

    # obtener el nombre de las columnas existentes
    fieldnames = csv_lectura.fieldnames + ['total_value']


    with open('ruta.csv' mode='w', newline='') as update_file
        csv_escribir = csv.DictWriter(update_file, fieldnames=fieldnames)
        csv_escribir.writeheader() # escribir encabezados

        for row in csv_reader:
            row['total_value'] = float(row['price']) * int(row['quantity'])
            csv_escribir.writerow(row)
```

:fire: json

`json` es un módulo en Python que permite trabajar con datos en formato JSON (JavaScript Object Notation). Se usa para convertir datos de Python a JSON y viceversa.

```python
import json

# Abrir archiv json
with open('ruta.json', mode='r') as file # Abre en variable file
    # cargar json como diccionario, nom_var se convierte en diccionario
    nom_variable_diccionario = json.load(file)

# agregar informacion a un json
nom_variable_diccionario.append({'key':'value'})

with open('ruta.sjon', mode='w') as file:
    json.dump(nom_variable_diccionario, file, indent=4)
```
