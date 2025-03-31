## Descargar archivos

https://getbootstrap.com/

Nombres de archivos

1. min -> archivo minificado

2. rtl -> archivo para desarrolladores que hacen codigo de derecha a izquierda

Para este caso voy a ocupar `bootstrap.min.css, bootstrap.min.css.map` y `bootstrap.bundle.min.js`

## Agregar bootstrap al HTML

```html
<head>
    <!-- CSS Bootstrap --->
    <link rel="stylesheet" href="ubicacion del archivo.css">
</head>
<body>
    <!-- JS Bootstrap --->
    <script src="></script>
</body>
```

## CSS Layout

La grid se divide en 12 columnas

1. Contenedores

```css
1. container
    Centra el el contenedor de forma horizontal.
2. container-tamaño
    Tamaño -> sm, md, lg, xl, xxl, fluid.
    Decidimos que hacer en caso de ciertos tamaños de pantalla
    con el contenedor, es decir ocupar todo el ancho o no.

3. container-fluid
    Abarca el 100% del ancho en todos los tamaños.
```

### Tamaño contenedores

|                    | Extra small (<576px) | Small (≥576px) | Medium (≥768px) | Large (≥992px) | X-Large (≥1200px) | XX-Large (≥1400px) |
| ------------------ | -------------------- | -------------- | --------------- | -------------- | ----------------- | ------------------ |
| `.container`       | 100%                 | 540px          | 720px           | 960px          | 1140px            | 1320px             |
| `.container-sm`    | 100%                 | 540px          | 720px           | 960px          | 1140px            | 1320px             |
| `.container-md`    | 100%                 | 100%           | 720px           | 960px          | 1140px            | 1320px             |
| `.container-lg`    | 100%                 | 100%           | 100%            | 960px          | 1140px            | 1320px             |
| `.container-xl`    | 100%                 | 100%           | 100%            | 100%           | 1140px            | 1320px             |
| `.container-xxl`   | 100%                 | 100%           | 100%            | 100%           | 100%              | 1320px             |
| `.container-fluid` | 100%                 | 100%           | 100%            | 100%           | 100%              | 100%               |

2. filas

```css
Estas se agregan dentro de un contenedor y el contenedor estara
tambien dividido en 12 columnas, de igual forma las filas.

sintaxis:
* row
# este define una fila de 12 columnas
<div class=row>
    <div class="col">Columna 1</div> # ocupa las 12 columnas
</div>

* row-cols-auto
# El ancho de las columnas que estan dentro de un row sera
# igual al ancho del contenido que contien.
<div class=row row-cols-auto>
    <div class="col">Granos</div>
    <div class="col">de</div>
    <div class="col">cafe</div>
    <div class="col">...</div>
</div>


rows-cols-numero
# Esto permite definir el numero de columnas que permitimos
# en una fila.

<div class=row row-cols-2>
    <div class="col">Columna 1</div>
    <div class="col">Columna 2</div>
    <div class="col">Columna 3</div>
    <div class="col">Columna 4</div>
</div>

rows-cols-tamaño-numero
# Este funciona de las mima forma que el anterior solo que podemos
# especificar los tamaños de pantalla.

    xs menos de 576px
    sm más de 576px y menos de 768px
    md más de 768px y menos de 992px
    lg más de 992px y menos de 1200px
    xl más de 1200px y menos de 1400px
    xxl más de 1400px
```

3. columnas

```css
Esta nos sirve para añadir columnas:

Sintaxis:
* col
    Divide las 12 columnas entre el numero de columnas que hay
        dentro de un row.

* col-auto
    El ancho del elemento/columna es igual a su contenido.

* col-numero
    El ancho de la columna es igual al ancho que proporcionemos.

* col-tamaño
    xs menos de 576px
    sm más de 576px y menos de 768px
    md más de 768px y menos de 992px
    lg más de 992px y menos de 1200px
    xl más de 1200px y menos de 1400px
    xxl más de 1400px

* col-tamaño-auto
    Esta clase casi no se utilizada devido a que es casi la misma
    funcion de col-auto, la diferencia radica en que especificamos
    un tamaño

* col-tamaño-numero
    class="col-12 col-md-6 col-lg-9" # columna 1
    class="col-12 col-md-6 col-lg-3" # columna 2

* w-100
    Permite dividir una fila por Num veces que necesitemos.
<div class=row>
    <div class="col-4">Columna 1</div>
    <div class="col-4">Columna 2</div>
    <div class="w-100"></div> # No se coloca nada dentro
    <div class="col-4">Columna 3</div>
    <div class="col-4">Columna 4</div>
</div>
```

4. Alineación

```css
# Esto permite alinea las columnas

Sintaxis:
eje-modo-ubicacion

Eje:
    - main axis -> justify # Horizontal
    - cross axis -> align # Vertical
Modo:  
    - content -> Grupo # Alinear de forma grupal
    - items -> Linea # Alinear line por liena
    - self -> Individual # Alinear de forma individual un elemento
Ubicacion:
    - align: start -> inicio
             center -> centro
             end -> fin
    - justify: start -> inicio # mueve el contenido a la izquierda
               center -> centro # mueve el contenido al centro
               end -> final # mueve el contenido a la derecha
               around -> alrededor # agrega espacios al rededor
               between -> entre # espacio entre cajas
               evenly -> igualmente # agrega el mismo espacio
                                    # alrededor

<div class="container">
    <div class="row">
        <h1>Alineacion de columnas</h1>
    </div>
    <div class="row eje-modo-ubicacion">
        <div class="col-3 eje-self-ubicacion">Columna 1</div>
        <div class="col-3">Columna 2</div>
        <div class="col-3">Columna 3</div>
    </div>
</div>
```

5. no-getters (g-0)

```css
# Esta clase se aplica a la clase que contenga la clase row
# Su funcion principal es eliminar los margenes
# que contiene la clase row

sintaxis:
# Ahora podemos agregar margenes
* Gutter en los cuatro lados
    g-valor
    g-pantall-valor

    Valor:
        0,1,2,3,4,5

    pantalla:
        xs, sm, md, lg, xl, xxl

* Gutter en horizontal
    gx-valor
    gx-pantalla-valor

    Valor:
        0,1,2,3,4,5

    pantalla:
        xs, sm, md, lg, xl, xxl

* GUtter en vertical
    gy-valor
    gy-pantall-valor

    Valor:
        0,1,2,3,4,5

    pantalla:
        xs, sm, md, lg, xl, xxl

<div class="container">
    <div class="row g-0">
        <div class="col-3">Columna 1</div>
        <div class="col-3">Columna 2</div>
        <div class="col-3">Columna 3</div>
    </div>
    <div class="row">
        <div class="col-3">Columna 1</div>
        <div class="col-3">Columna 2</div>
        <div class="col-3">Columna 3</div>
    </div>
</div>
```

6. Desplazamiento de columnas

```css
# Es desplazar una columna entre columnas, dos a la izquierda
# por ejemplo, o 6
sintaxis:
* offset -> se desplazan de izquierda a derecha
    offset-tamañoPantalla-numero

    tamañoPantalla -> opcional
    numero -> numero de columnas

* margin
    direccion-tamaño-auto

    direccion -> direccion del margion
        ms -> margin start # columa izquierda hacia la derecha
        me -> margin end # columna de dereacha hacia la izquierda

    tamaño -> opcional
        xs, sm, md, lg, xl, xxl
        
    auto -> palabra clave, obligatorio

<div class="container">
    <div class="row">
        <div class="col-3 offset-5">Columna 1</div>
    </div>
    <div class="row">
        <div class="col-3 ml-auto">Columna 1</div>
        <div class="col-3 mr-auto">Columna 2</div>
    </div>
</div>
```

7. re-ordenamiento

```css
# Esta propiedad aplica a las columnas y el valor por default
# de las col es 0, nos permite mover una columna
sintaxis:
    order-tamaño-numero

    tanaño -> opcional
        xs, sm, md, lg, xl, xxl

    numero -> de 1 a 5

    * order-tamaño-first -> pone la columna hasta el inicio -1

    * order-tamaño-last -> pone la columna hasta el final 6

<div class="container">
    <div class="row">
        <div class="col-2">1</div>
        <div class="col-2 order-1">2</div>
        <div class="col-2 order-2">3</div>
    </div>
</div>
```

8. Anidacion

```css
# Nos permite introducir columnas dentro de columnas
# para hacer eso, lo unico que debemos hacer
# es agregar una fila dentro de una columna y dentro
# de esta fila agregar mas columnas

<div class="container">
    <div class="row">
        <div class="col-6">1
            <div class="row">
                <div class="col">
                    Columna Anidada
                </div>
            </div>
        </div>
    </div>
</div>
```
