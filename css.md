**ESPECIFICIDAD**

```php
/*
    Especificidad -> Establece cómo de especifico es
    un selector para saber qué estilo aplicar.

    El cálculo se realiza con la siguiente formula:
    Etiquetas y pseudo-elementos: 0,0,1
    Clases, atributos y pseudo-clases: 0,1,0
    Ids: 1,0,0
    Estilos en line: 1,0,0,0
    !important: GANA A TODO -> no usar nunca

    h1 = 001 + .title = 011 + #title = 111
*/

h1.title#title{
    background-color: tomato;
}
```

---

**SELECETORES**

- Selectores Simples:
  - Selectores elementales:
    - Selector universal -> *
    - Selector de tipo o etiqueta -> Nombre de la etiqueta
  - Selectores de atributo:
    - id -> id del elemento (#nomId)
    - clase -> clase del elemento (.nomClase)
    - Otros atributos:
      - [nomAtributo]
      - [nomAtributo="valor"]
      - [nomAtributo^="valor"] -> valida si empieza
      - [nomAtributo*="valor"] -> no importa la posición
      - [nomAtributo$="valor"] -> si termina
      - [nomAtributo|="valor"]
- Selectores Compuestos:
  - Selectores Agrupados
  - Selectores Combinadores:
    - Selector descendiente/hijo
    - Selector de hermano siguiente (+)
    - Selector de hermanos siguientes (~)
    - Selector de hijo directo (>)
  - Pseudoclases - Pseudoelementos

```php
/*
    Selector universal:
    lo que hace es seleccionar todo, casos concretos.
*/
*{
    background-color: aquamarine;
}

/*
    Selector de etiqueta:
    Es solo el nombre de la etiqueta,se suele
    utilizar para el reinicio de estilos.
*/
p{
    background-color: lightgreen;
}

/* 
    Selector de id
    Este selector es case sensitive
    id="title"
*/
#title{
    background-color: lightgreen;
}

/*
    Selector de clase
    Este selector es case sensitive
    class="title"
*/
.title{
    background-color: lightsalmon;
}

/*
    Selector de atributo [nomAtributo]
    href=""
*/
[href]{
    background-color: lightgreen;
}

/*
    Selector de atributo con valor [nomAtributo=valor]
    href="www.google.com"
*/
[href="www.google.com"]{
    background-color: teal;
}

/*
    Selector de atributo que valida si empieza por dicho valor
    [nomAtributo^="valor"] -> se seleccionara todas las coincidencias
    que comience por dicho valor.
    href="color-rojo"
    href="color-blue"
*/
[href^="color"]{
    background-color: red;
}

/*
    Selector de atributo al cual no le importa la posición del valor,
    lo importante es que este.
    [href="nomAtribut*="valor"]
    href="inicio-blanco-color"
*/
[href*="color"]{
    background-color: green;
}

/*
    Selector de atributo por terminación de valor, es decir;
    busca donde termine el valor.
    [href$="valor"]
    href="inicio-medio-final";
*/
[href$="final"]{
    background-color: blue;
}

/*
    Selector de atributo por |, este selector selecciona
    aquellas coincidencias que puedan tener un "-" ejemplo en-, no
    también selecciona aquellas que no tienen es "-"
    [nomAtributo|="valor"]
    <p lang="en">texto de prueba</p>
*/
[lang|="en"]{
    background-color: magenta;
}

/*
    Selectores Compuestos:
    son aquellos que requieren mas de una palabra, un palabra
    y un símbolo. esto agrupa estilos.
    selector,
    selector,
    selector{
        estilos
    }
    <p class="text">lorem</p>
    <p class="text-2">lorem</p>
    <p class="text-3">lorem</p>
*/
texto,
texto-2,
texto-3{
    background-color: steelblue;
}

/*
    Selector descendiente/selector hijos:
    Este selector nos permite seleccionar las coincidencias
    dentro de otro.
    <div>
        <p class="title">lorem</p>
        <p class="title">lorem</p>
    </div>
    No hay limite de descendencia, pero no es recomendable
    bajar mas de un nivel, es decir hasta donde esta el ejemplo.
    selector selector{
        estilos
    }
*/
div .title{
    background-color: teal;
}

/*
    Selector de hermano siguiente, es
    decir selecciona aquellos que están al mismo nivel.
    <p class="texto">lorem</p>
    <h2 class="titulo">titulo</h2>
    selector + selector{
        estilos
    }
*/
.texto + .titulo{
    background-color: tomato;
}

/*
    Selector de hermanos siguientes.
    Selecciona todos los hermanos del mismo nivel que sean igual
    al selector.
    <p class="texto">lorem</p>
    <h2 class="titulo">titulo</h2>
    <p class="texto">lorem</p>
    selector ~ selectorHermanos{
        estilos
    }
*/
.texto ~ p{
    background-color: teal;
}

/*
    Selector de hijo directo, solo selecciona
    el primer hijo
    <div class="container">
        <p class="title">lorem</p>
    </div>
    selector > selectorHijoDirecto{
        estilos
    }
*/
.container > p{
    background-color: tomato;
}
```

---

**PROPIEDADES**

:fire: **display**

```css
/*
    La propiedad display nos sirve para cambiar el contexto de
    los elementos dentro del navegador.

    Admite varios valores:
        none -> Hace que el elemento no se muestre, pero
            sigue cargandose.
        block -> Hace que el elemento sea de bloque.
        inline -> Hace que el elemento sea de liena.
        inline-block -> Hace que el elemento sea de linea pero
            admite medidas y margenes verticales.
*/
```

:fire: **outline**

```css
/*
    Outline es la propiedad que nos permite dibujar un borde por fuera
        del modelo de caja.

    Es un shorthuand que engloba:
        outline-width: Controla el ancho del outline
        outline-styel: Controla el estilo del outline
        outline-color: Controla el color del outline

    Tiene las mismas propiedades y sintaxis que border,
        Pero con algunas diferencias:

    * No ocupa sitio, ya que no forma parte del box-model
    * No se puede redondear
    * No se pueden controlar los lados de forma independientel.

    Tambien cuenta con la propiedad outline-offset, que nos permite
    aumentar o dimsminuir la distancia del outline en relacion
    a la caja a la que pertenece.
*/
```

:fire: **text-align**

```css
/*
    text-align: es la propiedad que nos permite alinear
    horizontalmente el contenido de un elemento de bloque
    siempre que el contenido NO TENGA ANCHO DECLARADO.

    Acepta 4 posibles valores.
        text-align: left; Aliena el contenido a la izquierda
        text-align: right; Alinea el contenido a la derecha
        text-align: center; Alinea el contenido al centro
        text-align: justify; Alinea el contenido de forma
            justificado. No es recomendado usarlo.
*/
```

:fire: **box-shadow**

```css
/*
    La propiedad box-shadow se creó para añadir efectos de
    sombra a nuestra caja.

    En esencia lo que hace es crear un clon de la caja
    respetando la forma de su box-model (ancho-alto-rendondez)

    La sintaxis de box-shadow se puede escribir de distintas
    formas segun lo que queramos conseguir.
    Los valores que le podemos poner son:
        * offset-x -> Desplazamiento en x (obligatorio)
        * offset-y -> Desplazamiento en y (obligatorio)
        * blur-radius -> Desenfoque de la sombra
        * spread-radius -> Expansion de la sombra
        * color -> El color de la sombra, si no lo
            especificamos lo heredara del elemeno al que
            pertenece.
        * inset -> Determina si la sombra será interior o
            exterior.
*/
box-shadow: inset x y blur color spread, otra-sombra;
```

:fire: **position**

```css
/*
    La propiedad position nos permite posicionar los elementos.
    Hay algunos conceptos que debeis conocoer para entender esto.

    Flujo de renderizado -> Por norma general los elementos se
    dibujan de izquierda a derecha y de arriba abajo. El punto 0,0
    de los elementos, por norma general, es la esquina superior
    izquierda.

    Espacio reservado -> Es el espacio que tiene un elemento asignado
    en el navegador.

    Elemento posicionado -> Esto significa que el elemento tiene
    la propiedad position con un valor distinto de 'static', que
    es el valor que tiene esta propiedad por defecto.

    stackin context -> COntexto de ampliamiento. Es el orden en
    el que se aplicarán las cajas que se superponen.

    Al posicionar un elemento se habilitan 5 propiedades que podemos
    utilizar para mover los elementos en los 3 ejes.

        top -> El elemento se movera desde la parta superior la
            distancia que le hayamos indicado.

        right -> El elemento se movera desde la parte derecha
            la distancia que le hayamos indicado.

        bottom -> El elemento se movera desde la parte inferior
            la distancia que la hayamos indicado.

        left -> El elemento se movera desde la parte izquierda
            la distancia que le hayamos indicado.

        z-index -> Nos permite mover el elemento en el
            contexto de apilamiento (eje z)

        NOTA: si a un elemento le declaramos la propiedad
        top y/o left, las propiedades bottom y/0 right no funcionaran.

    Los posibles valores que le podemos dar a position son.

    * Static -> Es el valor que tiene por defecto un elemento,
        con este valor el elemento NO ESTA POSICIONADO y por
        lo cual no podremos moverlo.

    * relative -> El elemento perdera sus medidas y su espacio
        reservado. Si lo movemos usara el elemento padre
        posicionando como referencia. Si lo movemos lo hara usando
        su posicion en el html como punto de referencia.

    * Absolute -> El elemento perdera sus medidas y su espacio
        reservado. Si lo movemos usara el elemento padre
        posicionado como referencia. Si no tiene ninguno,
        usará el elemento html de referencia.

    * Fixed -> El elemento perdera sus medidas y su espacio
        reservado. Si lo movemos usara el elemento html de
        referencia, y además se quedara fijo en esa posicion
        aunque hagamos scroll.

    * sticky -> Es una mezcla de position relative y fixed.
        Con este tipo de posicionamiento los valores top, left,
        bottom y right no sirven para mover el elemento, si no
        para indicarle en que punto pasar a tener un comportamiento
        de posicionamiento fixed, hasta llegar a ese punto se
        comportara como si tuviera relative.
*/
```
