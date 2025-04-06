```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Markdown/docs/src/index.md"
```

# [Markdown](@id markdown_stdlib)

Esta sección describe la sintaxis de markdown de Julia, que está habilitada por la biblioteca estándar Markdown. Los siguientes elementos de Markdown son compatibles:

## Inline elements

Aquí "en línea" se refiere a elementos que se pueden encontrar dentro de bloques de texto, es decir, párrafos. Estos incluyen los siguientes elementos.

### Bold

Rodear palabras con dos asteriscos, `**`, para mostrar el texto encerrado en negrita.

```
A paragraph containing a **bold** word.
```

### Italics

Rodear palabras con un asterisco, `*`, para mostrar el texto encerrado en cursiva.

```
A paragraph containing an *italicized* word.
```

### Literals

Rodear el texto que debe mostrarse exactamente como está escrito con comillas simples invertidas, ``` ` ```.

```
A paragraph containing a `literal` word.
```

Los literales deben usarse al escribir texto que se refiere a nombres de variables, funciones u otras partes de un programa en Julia.

!!! tip
    Para incluir un carácter de comilla invertida dentro del texto literal, utiliza tres comillas invertidas en lugar de una para encerrar el texto.

    ```
    A paragraph containing ``` `backtick` characters ```.
    ```

    Por extensión, se puede usar cualquier número impar de comillas invertidas para encerrar un número menor de comillas invertidas.


### $\LaTeX$

Rodear el texto que debe mostrarse como matemáticas utilizando la sintaxis de $\LaTeX$ con dobles comillas invertidas, ``` `` ```.

```
A paragraph containing some ``\LaTeX`` markup.
```

!!! tip
    Al igual que con los literales en la sección anterior, si se necesitan escribir comillas invertidas literales dentro de comillas invertidas dobles, utiliza un número par mayor que dos. Ten en cuenta que si se necesita incluir una sola comilla invertida literal dentro del marcado de $\LaTeX$, entonces dos comillas invertidas de cierre son suficientes.


!!! note
    El carácter `\` debe ser escapado adecuadamente si el texto está incrustado en un código fuente de Julia, por ejemplo, ```"``\\LaTeX`` sintaxis en un docstring."```, ya que se interpreta como un literal de cadena. Alternativamente, para evitar el escape, es posible usar el macro de cadena `raw` junto con el macro `@doc`:

    ```
    @doc raw"``\LaTeX`` syntax in a docstring." functionname
    ```


### Links

Los enlaces a objetivos externos o internos se pueden escribir utilizando la siguiente sintaxis, donde el texto encerrado entre corchetes, `[ ]`, es el nombre del enlace y el texto encerrado entre paréntesis, `( )`, es la URL.

```
A paragraph containing a link to [Julia](https://www.julialang.org).
```

También es posible agregar referencias cruzadas a otras funciones/métodos/variables documentados dentro de la propia documentación de Julia. Por ejemplo:

```julia
"""
    tryparse(type, str; base)

Like [`parse`](@ref), but returns either a value of the requested type,
or [`nothing`](@ref) if the string does not contain a valid number.
"""
```

Esto creará un enlace en la documentación generada a la documentación de [`parse`](@ref) (que tiene más información sobre lo que realmente hace esta función), y a la documentación de [`nothing`](@ref). Es bueno incluir referencias cruzadas a versiones mutantes/no mutantes de una función, o resaltar una diferencia entre dos funciones que parecen similares.

!!! note
    La referencia cruzada anterior *no* es una característica de Markdown y se basa en [Documenter.jl](https://github.com/JuliaDocs/Documenter.jl), que se utiliza para construir la documentación base de Julia.


### Footnote references

Las referencias de notas al pie nombradas y numeradas se pueden escribir utilizando la siguiente sintaxis. Un nombre de nota al pie debe ser una sola palabra alfanumérica que no contenga puntuación.

```
A paragraph containing a numbered footnote [^1] and a named one [^named].
```

!!! note
    El texto asociado con una nota al pie se puede escribir en cualquier lugar dentro de la misma página que la referencia de la nota al pie. La sintaxis utilizada para definir el texto de la nota al pie se discute en la sección [Footnotes](@ref) a continuación.


## Toplevel elements

Los siguientes elementos pueden escribirse ya sea en el "nivel superior" de un documento o dentro de otro elemento "nivel superior".

### Paragraphs

Un párrafo es un bloque de texto plano, que puede contener cualquier número de elementos en línea definidos en la sección [Inline elements](@ref) anterior, con una o más líneas en blanco arriba y abajo.

```
This is a paragraph.

And this is *another* paragraph containing some emphasized text.
A new line, but still part of the same paragraph.
```

### Headers

Un documento se puede dividir en diferentes secciones utilizando encabezados. Los encabezados utilizan la siguiente sintaxis:

```julia
# Level One
## Level Two
### Level Three
#### Level Four
##### Level Five
###### Level Six
```

Una línea de encabezado puede contener cualquier sintaxis en línea de la misma manera que un párrafo puede.

!!! tip
    Intenta evitar usar demasiados niveles de encabezado dentro de un solo documento. Un documento con una estructura de encabezados muy anidada puede ser indicativo de la necesidad de reestructurarlo o dividirlo en varias páginas que cubran temas separados.


### Code blocks

El código fuente se puede mostrar como un bloque literal utilizando una sangría de cuatro espacios o una tabulación, como se muestra en el siguiente ejemplo.

```
This is a paragraph.

    function func(x)
        # ...
    end

Another paragraph.
```

Además, los bloques de código se pueden encerrar utilizando tres acentos graves con un "lenguaje" opcional para especificar cómo se debe resaltar un bloque de código.

````
A code block without a "language":

```
function func(x)
    # ...
end
```

and another one with the "language" specified as `julia`:

```julia
function func(x)
    # ...
end
```
````

!!! note
    Los bloques de código "fenceados", como se muestra en el último ejemplo, deben ser preferidos sobre los bloques de código indentados ya que no hay forma de especificar en qué lenguaje está escrito un bloque de código indentado.


### Block quotes

El texto de fuentes externas, como citas de libros o sitios web, se puede citar utilizando caracteres `>` precedidos a cada línea de la cita de la siguiente manera.

```
Here's a quote:

> Julia is a high-level, high-performance dynamic programming language for
> technical computing, with syntax that is familiar to users of other
> technical computing environments.
```

Nota que debe aparecer un solo espacio después del carácter `>` en cada línea. Los bloques citados pueden contener otros elementos de nivel superior o elementos en línea.

### Images

La sintaxis para imágenes es similar a la sintaxis de enlaces mencionada anteriormente. Anteponer un carácter `!` a un enlace mostrará una imagen de la URL especificada en lugar de un enlace a ella.

```julia
![alternative text](link/to/image.png)
```

### Lists

Las listas desordenadas se pueden escribir anteponiendo a cada elemento de una lista ya sea `*`, `+` o `-`.

```
A list of items:

  * item one
  * item two
  * item three
```

Nota los dos espacios antes de cada `*` y el único espacio después de cada uno.

Las listas pueden contener otros elementos de nivel superior anidados, como listas, bloques de código o bloques de citas. Se debe dejar una línea en blanco entre cada elemento de la lista al incluir cualquier elemento de nivel superior dentro de una lista.

```
Another list:

  * item one

  * item two

    ```
    f(x) = x
    ```

  * And a sublist:

      + sub-item one
      + sub-item two
```

!!! note
    El contenido de cada elemento en la lista debe alinearse con la primera línea del elemento. En el ejemplo anterior, el bloque de código cercado debe estar indentado por cuatro espacios para alinearse con la `i` en `elemento dos`.


Las listas ordenadas se escriben reemplazando el carácter "viñeta", ya sea `*`, `+` o `-`, con un número entero positivo seguido de `.` o `)`.

```
Two ordered lists:

 1. item one
 2. item two
 3. item three

 5) item five
 6) item six
 7) item seven
```

Una lista ordenada puede comenzar desde un número diferente a uno, como en la segunda lista del ejemplo anterior, donde se numera desde cinco. Al igual que con las listas desordenadas, las listas ordenadas pueden contener elementos de nivel superior anidados.

### Display equations

Las grandes ecuaciones de $\LaTeX$ que no encajan en línea dentro de un párrafo pueden escribirse como ecuaciones en display utilizando un bloque de código cercado con el "lenguaje" `math`, como en el ejemplo a continuación.

````julia
```math
f(a) = \frac{1}{2\pi}\int_{0}^{2\pi} (\alpha+R\cos(\theta))d\theta
```
````

### Footnotes

Esta sintaxis se empareja con la sintaxis en línea para [Footnote references](@ref). Asegúrate de leer esa sección también.

El texto de la nota al pie se define utilizando la siguiente sintaxis, que es similar a la sintaxis de referencia de notas al pie, aparte del carácter `:` que se añade a la etiqueta de la nota al pie.

```
[^1]: Numbered footnote text.

[^note]:

    Named footnote text containing several toplevel elements
    indented by 4 spaces or one tab.

      * item one
      * item two
      * item three

    ```julia
    function func(x)
        # ...
    end
    ```
```

!!! note
    No se realizan verificaciones durante el análisis para asegurarse de que todas las referencias de notas al pie tengan notas al pie coincidentes.


### Horizontal rules

El equivalente de una etiqueta HTML `<hr>` se puede lograr utilizando tres guiones (`---`). Por ejemplo:

```
Text above the line.

---

And text below the line.
```

### Tables

Las tablas básicas se pueden escribir utilizando la sintaxis descrita a continuación. Tenga en cuenta que las tablas de markdown tienen características limitadas y no pueden contener elementos de nivel superior anidados, a diferencia de otros elementos discutidos anteriormente; solo se permiten elementos en línea. Las tablas siempre deben contener una fila de encabezado con los nombres de las columnas. Las celdas no pueden abarcar múltiples filas o columnas de la tabla.

```
| Column One | Column Two | Column Three |
|:---------- | ---------- |:------------:|
| Row `1`    | Column `2` |              |
| *Row* 2    | **Row** 2  | Column ``3`` |
```

!!! note
    Como se ilustra en el ejemplo anterior, cada columna de caracteres `|` debe estar alineada verticalmente.

    Un carácter `:` en cualquiera de los extremos del separador del encabezado de una columna (la fila que contiene caracteres `-`) especifica si la fila está alineada a la izquierda, alineada a la derecha, o (cuando `:` aparece en ambos extremos) alineada al centro. No proporcionar caracteres `:` alineará la columna a la derecha por defecto.


### Admonitions

Bloques especialmente formateados, conocidos como admoniciones, se pueden usar para resaltar comentarios particulares. Se pueden definir utilizando la siguiente sintaxis `!!!`:

```
!!! note

    This is the content of the note.
    It is indented by 4 spaces. A tab would work as well.

!!! warning "Beware!"

    And this is another one.

    This warning admonition has a custom title: `"Beware!"`.
```

La primera palabra después de `!!!` declara el tipo de la admonición. Hay tipos de admonición estándar que deben producir un estilo especial. A saber (en orden de gravedad decreciente): `peligro`, `advertencia`, `información`/`nota`, y `consejo`.

También puedes usar tus propios tipos de admonición, siempre que el nombre del tipo contenga solo caracteres latinos en minúsculas (a-z). Por ejemplo, podrías tener un bloque de `terminología` como este:

```
!!! terminology "julia vs Julia"

    Strictly speaking, "Julia" refers to the language,
    and "julia" to the standard implementation.
```

Sin embargo, a menos que el código que renderiza el Markdown trate ese tipo de admonición de manera especial, obtendrá el estilo predeterminado.

Se puede proporcionar un título personalizado para el cuadro como una cadena (entre comillas dobles) después del tipo de admonición. Si no se especifica texto de título después del tipo de admonición, entonces se utilizará el nombre del tipo como título (por ejemplo, `"Nota"` para la admonición `nota`).

Las admoniciones, como la mayoría de los otros elementos de nivel superior, pueden contener otros elementos de nivel superior (por ejemplo, listas, imágenes).

## [Markdown String Literals](@id stdlib-markdown-literals)

El `md""` macro te permite incrustar cadenas de Markdown directamente en tu código Julia. Este macro está diseñado para simplificar la inclusión de texto con formato Markdown dentro de tus archivos fuente de Julia.

### Usage

```julia
result = md"This is a **custom** Markdown string with [a link](http://example.com)."
```

## Markdown Syntax Extensions

El markdown de Julia admite la interpolación de una manera muy similar a los literales de cadena básicos, con la diferencia de que almacenará el objeto en sí en el árbol de Markdown (en lugar de convertirlo en una cadena). Cuando se renderiza el contenido de Markdown, se llamarán a los métodos `show` habituales, y estos se pueden sobrescribir como de costumbre. Este diseño permite que el Markdown se extienda con características arbitrariamente complejas (como referencias) sin desordenar la sintaxis básica.

En principio, el propio analizador de Markdown también puede ser ampliado arbitrariamente por paquetes, o se puede utilizar un sabor completamente personalizado de Markdown, pero esto generalmente debería ser innecesario.

## [API reference](@id stdlib-markdown-api)

```@docs
Markdown.MD
Markdown.@md_str
Markdown.@doc_str
Markdown.html
Markdown.latex
```
