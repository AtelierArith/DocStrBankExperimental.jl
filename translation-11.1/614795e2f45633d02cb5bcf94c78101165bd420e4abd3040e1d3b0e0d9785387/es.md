# [Documentation](@id man-documentation)

## Accessing Documentation

La documentación se puede acceder en el REPL o en [IJulia](https://github.com/JuliaLang/IJulia.jl) escribiendo `?` seguido del nombre de una función o macro, y presionando `Enter`. Por ejemplo,

```julia
?cos
?@time
?r""
```

mostrará la documentación para la función, macro o macro de cadena relevante respectivamente. La mayoría de los entornos de Julia proporcionan una forma de acceder a la documentación directamente:

  * [VS Code](https://www.julia-vscode.org/) muestra la documentación cuando pasas el cursor sobre el nombre de una función. También puedes usar el panel de Julia en la barra lateral para buscar documentación.
  * En [Pluto](https://github.com/fonsp/Pluto.jl), abre el panel "Live Docs" en la esquina inferior derecha.
  * En [Juno](https://junolab.org), usar `Ctrl-J, Ctrl-D` mostrará la documentación para el objeto bajo el cursor.

`Docs.hasdoc(module, name)::Bool` indica si un nombre tiene una cadena de documentación. `Docs.undocumented_names(module; all)` devuelve los nombres no documentados en un módulo.

## Writing Documentation

Julia permite a los desarrolladores de paquetes y a los usuarios documentar funciones, tipos y otros objetos fácilmente a través de un sistema de documentación integrado.

La sintaxis básica es simple: cualquier cadena que aparezca justo antes de un objeto (función, macro, tipo o instancia) se interpretará como documentación de este (se les llama *docstrings*). Tenga en cuenta que no puede haber líneas en blanco ni comentarios entre un docstring y el objeto documentado. Aquí hay un ejemplo básico:

```julia
"Tell whether there are too foo items in the array."
foo(xs::Array) = ...
```

La documentación se interpreta como [Markdown](https://en.wikipedia.org/wiki/Markdown), por lo que puedes usar la indentación y los bloques de código para delimitar ejemplos de código del texto. Técnicamente, cualquier objeto puede asociarse con cualquier otro como metadatos; Markdown resulta ser el predeterminado, pero también se pueden construir otros macros de cadena y pasarlos al macro `@doc` de la misma manera.

!!! note
    El soporte de Markdown está implementado en la biblioteca estándar `Markdown` y para una lista completa de la sintaxis soportada, consulta el [documentation](@ref markdown_stdlib).


Aquí hay un ejemplo más complejo, aún utilizando Markdown:

````julia
"""
    bar(x[, y])

Compute the Bar index between `x` and `y`.

If `y` is unspecified, compute the Bar index between all pairs of columns of `x`.

# Examples
```julia-repl
julia> bar([1, 2], [1, 2])
1
```
"""
function bar(x, y) ...
````

Como en el ejemplo anterior, recomendamos seguir algunas convenciones simples al escribir documentación:

1. Siempre muestra la firma de una función en la parte superior de la documentación, con una sangría de cuatro espacios para que se imprima como código Julia.

    Esto puede ser idéntico a la firma presente en el código de Julia (como `mean(x::AbstractArray)`), o una forma simplificada. Los argumentos opcionales deben representarse con sus valores predeterminados (es decir, `f(x, y=1)`) cuando sea posible, siguiendo la sintaxis real de Julia. Los argumentos opcionales que no tienen un valor predeterminado deben colocarse entre corchetes (es decir, `f(x[, y])` y `f(x[, y[, z]])`). Una solución alternativa es usar varias líneas: una sin argumentos opcionales, la(s) otra(s) con ellos. Esta solución también se puede utilizar para documentar varios métodos relacionados de una función dada. Cuando una función acepta muchos argumentos de palabra clave, solo incluye un marcador de posición `<argumentos de palabra clave>` en la firma (es decir, `f(x; <argumentos de palabra clave>)`), y proporciona la lista completa en una sección `# Argumentos` (ver punto 4 a continuación).
2. Incluye una única oración en una línea que describa lo que hace la función o lo que representa el objeto después del bloque de firma simplificado. Si es necesario, proporciona más detalles en un segundo párrafo, después de un espacio en blanco.

    La oración de una línea debe usar la forma imperativa ("Haz esto", "Devuelve eso") en lugar de la tercera persona (no escribas "Devuelve la longitud...") al documentar funciones. Debe terminar con un punto. Si el significado de una función no se puede resumir fácilmente, dividirla en partes composables separadas podría ser beneficioso (esto no debe tomarse como un requisito absoluto para cada caso en particular).
3. No te repitas.

    Dado que el nombre de la función se proporciona en la firma, no es necesario comenzar la documentación con "La función `bar`...": ve directo al grano. De manera similar, si la firma especifica los tipos de los argumentos, mencionarlos en la descripción es redundante.
4. Solo proporciona una lista de argumentos cuando sea realmente necesario.

    Para funciones simples, a menudo es más claro mencionar el papel de los argumentos directamente en la descripción del propósito de la función. Una lista de argumentos solo repetiría información ya proporcionada en otro lugar. Sin embargo, proporcionar una lista de argumentos puede ser una buena idea para funciones complejas con muchos argumentos (en particular, argumentos de palabra clave). En ese caso, insértala después de la descripción general de la función, bajo un encabezado `# Argumentos`, con un viñeta `-` para cada argumento. La lista debe mencionar los tipos y los valores predeterminados (si los hay) de los argumentos:

    ```julia
    """
    ...
    # Arguments
    - `n::Integer`: the number of elements to compute.
    - `dim::Integer=1`: the dimensions along which to perform the computation.
    ...
    """
    ```
5. Proporcione pistas sobre funciones relacionadas.

    A veces hay funciones de funcionalidad relacionada. Para aumentar la capacidad de descubrimiento, por favor proporciona una lista corta de estas en un párrafo de `Ver también`.

    ```
    See also [`bar!`](@ref), [`baz`](@ref), [`baaz`](@ref).
    ```
6. Include any code examples in an `# Examples` section.

    Examples should, whenever possible, be written as *doctests*. A *doctest* is a fenced code block (see [Code blocks](@ref)) starting with ````` ```jldoctest````` and contains any number of `julia>` prompts together with inputs and expected outputs that mimic the Julia REPL.

    !!! note
        Los doctests están habilitados por [`Documenter.jl`](https://github.com/JuliaDocs/Documenter.jl). Para una documentación más detallada, consulte el [manual](https://juliadocs.github.io/Documenter.jl/) del Documentador.


    Por ejemplo, en el siguiente docstring se define una variable `a` y el resultado esperado, tal como se imprime en un REPL de Julia, aparece a continuación:

    ````julia
    """
    Some nice documentation here.

    # Examples
    ```jldoctest
    julia> a = [1 2; 3 4]
    2×2 Array{Int64,2}:
     1  2
     3  4
    ```
    """
    ````

    !!! warning
        Llamar a `rand` y otras funciones relacionadas con RNG debe evitarse en doctests, ya que no producirán salidas consistentes durante diferentes sesiones de Julia. Si deseas mostrar alguna funcionalidad relacionada con la generación de números aleatorios, una opción es construir y sembrar explícitamente tu propio objeto RNG (ver [`Random`](@ref Random-Numbers)) y pasarlo a las funciones que estás probando en los doctests.

        El tamaño de palabra del sistema operativo ([`Int32`](@ref) o [`Int64`](@ref)) así como las diferencias en el separador de rutas (`/` o `\`) también afectarán la reproducibilidad de algunas pruebas de documentos.

        ¡Ten en cuenta que el espacio en blanco en tu doctest es significativo! El doctest fallará si desalineas la salida de la impresión bonita de un array, por ejemplo.


    Puedes ejecutar `make -C doc doctest=true` para ejecutar todas las pruebas de documentación en el Manual de Julia y la documentación de la API, lo que asegurará que tu ejemplo funcione.

    Para indicar que el resultado de salida está truncado, puedes escribir `[...]` en la línea donde se debe detener la verificación. Esto es útil para ocultar un stacktrace (que contiene referencias no permanentes a líneas de código julia) cuando el doctest muestra que se lanza una excepción, por ejemplo:

    ````julia
    ```jldoctest
    julia> div(1, 0)
    ERROR: DivideError: integer division error
    [...]
    ```
    ````

    Ejemplos que no son verificables deben escribirse dentro de bloques de código delimitados que comienzan con ````` ```julia````` para que se resalten correctamente en la documentación generada.

    !!! tip
        Donde sea posible, los ejemplos deben ser **autónomos** y **ejecutables** para que los lectores puedan probarlos sin tener que incluir ninguna dependencia.
7. Usa comillas invertidas para identificar código y ecuaciones.

    Los identificadores de Julia y los fragmentos de código deben aparecer siempre entre comillas invertidas ``` ` ``` para habilitar el resaltado. Las ecuaciones en la sintaxis de LaTeX se pueden insertar entre comillas dobles invertidas ``` `` ```. Utiliza caracteres Unicode en lugar de su secuencia de escape de LaTeX, es decir, ``` ``α = 1`` ``` en lugar de ``` ``\\alpha = 1`` ```.
8. Place the starting and ending `"""` characters on lines by themselves.

    Eso es, escribe:

    ```julia
    """
    ...

    ...
    """
    f(x, y) = ...
    ```

    en lugar de:

    ```julia
    """...

    ..."""
    f(x, y) = ...
    ```

    Esto hace más claro dónde comienzan y terminan las cadenas de documentación.
9. Respete el límite de longitud de línea utilizado en el código circundante.

    Las cadenas de documentación se editan utilizando las mismas herramientas que el código. Por lo tanto, las mismas convenciones deberían aplicarse. Se recomienda que las líneas tengan un máximo de 92 caracteres de ancho.
10. Proporcione información que permita a los tipos personalizados implementar la función en una sección de `# Implementación`. Estos detalles de implementación están destinados a desarrolladores en lugar de usuarios, explicando, por ejemplo, qué funciones deben ser sobrescritas y qué funciones utilizan automáticamente alternativas apropiadas. Tales detalles son mejor mantenerlos separados de la descripción principal del comportamiento de la función.
11. Para docstrings largas, considera dividir la documentación con un encabezado `# Ayuda extendida`. El modo de ayuda típico mostrará solo el material por encima del encabezado; puedes acceder a la ayuda completa añadiendo un '?' al principio de la expresión (es decir, "??foo" en lugar de "?foo").

## Functions & Methods

Las funciones en Julia pueden tener múltiples implementaciones, conocidas como métodos. Si bien es una buena práctica que las funciones genéricas tengan un solo propósito, Julia permite que los métodos se documenten individualmente si es necesario. En general, solo el método más genérico debe ser documentado, o incluso la función en sí (es decir, el objeto creado sin ningún método por `function bar end`). Los métodos específicos solo deben documentarse si su comportamiento difiere de los más genéricos. En cualquier caso, no deben repetir la información proporcionada en otros lugares. Por ejemplo:

```julia
"""
    *(x, y, z...)

Multiplication operator. `x * y * z *...` calls this function with multiple
arguments, i.e. `*(x, y, z...)`.
"""
function *(x, y, z...)
    # ... [implementation sold separately] ...
end

"""
    *(x::AbstractString, y::AbstractString, z::AbstractString...)

When applied to strings, concatenates them.
"""
function *(x::AbstractString, y::AbstractString, z::AbstractString...)
    # ... [insert secret sauce here] ...
end

help?> *
search: * .*

  *(x, y, z...)

  Multiplication operator. x * y * z *... calls this function with multiple
  arguments, i.e. *(x,y,z...).

  *(x::AbstractString, y::AbstractString, z::AbstractString...)

  When applied to strings, concatenates them.
```

Al recuperar la documentación para una función genérica, los metadatos de cada método se concatenan con la función `catdoc`, que por supuesto se puede sobrescribir para tipos personalizados.

## Advanced Usage

El macro `@doc` asocia su primer argumento con su segundo en un diccionario por módulo llamado `META`.

Para facilitar la redacción de la documentación, el analizador trata el nombre de macro `@doc` de manera especial: si una llamada a `@doc` tiene un argumento, pero aparece otra expresión después de un salto de línea simple, entonces esa expresión adicional se agrega como un argumento a la macro. Por lo tanto, la siguiente sintaxis se analiza como una llamada de 2 argumentos a `@doc`:

```julia
@doc raw"""
...
"""
f(x) = x
```

Esto hace posible utilizar expresiones distintas de los literales de cadena normales (como el macro de cadena `raw""`) como docstring.

Cuando se utiliza para recuperar documentación, el macro `@doc` (o igualmente, la función `doc`) buscará en todos los diccionarios `META` la metadata relevante para el objeto dado y la devolverá. El objeto devuelto (algún contenido en Markdown, por ejemplo) se mostrará de manera inteligente por defecto. Este diseño también facilita el uso del sistema de documentación de manera programática; por ejemplo, para reutilizar documentación entre diferentes versiones de una función:

```julia
@doc "..." foo!
@doc (@doc foo!) foo
```

O para usar con la funcionalidad de metaprogramación de Julia:

```julia
for (f, op) in ((:add, :+), (:subtract, :-), (:multiply, :*), (:divide, :/))
    @eval begin
        $f(a, b) = $op(a, b)
    end
end
@doc "`add(a, b)` adds `a` and `b` together" add
@doc "`subtract(a, b)` subtracts `b` from `a`" subtract
```

La documentación en bloques que no son de nivel superior, como `begin`, `if`, `for`, `let` y constructores internos, también debe añadirse al sistema de documentación a través de `@doc`. Por ejemplo:

```julia
if condition()
    @doc "..."
    f(x) = x
end
```

agregará documentación a `f(x)` cuando `condition()` sea `true`. Tenga en cuenta que, incluso si `f(x)` sale del alcance al final de un bloque, su documentación permanecerá.

Es posible hacer uso de la metaprogramación para ayudar en la creación de documentación. Al usar la interpolación de cadenas dentro de la cadena de documentación, necesitarás usar un `$` adicional como se muestra con `$($name)`:

```julia
for func in (:day, :dayofmonth)
    name = string(func)
    @eval begin
        @doc """
            $($name)(dt::TimeType) -> Int64

        The day of month of a `Date` or `DateTime` as an `Int64`.
        """ $func(dt::Dates.TimeType)
    end
end
```

### Dynamic documentation

A veces, la documentación apropiada para una instancia de un tipo depende de los valores de los campos de esa instancia, en lugar de depender solo del tipo en sí. En estos casos, puedes agregar un método a `Docs.getdoc` para tu tipo personalizado que devuelva la documentación de manera específica para cada instancia. Por ejemplo,

```julia
struct MyType
    value::Int
end

Docs.getdoc(t::MyType) = "Documentation for MyType with value $(t.value)"

x = MyType(1)
y = MyType(2)
```

`?x` mostrará "Documentación para MyType con valor 1" mientras que `?y` mostrará "Documentación para MyType con valor 2".

## Syntax Guide

Esta guía proporciona una visión general completa de cómo adjuntar documentación a todos los constructos de sintaxis de Julia para los cuales es posible proporcionar documentación.

En los siguientes ejemplos, `"..."` se utiliza para ilustrar una cadena de documentación arbitraria.

### `$` and `\` characters

Los caracteres `$` y `\` todavía se interpretan como interpolación de cadenas o el inicio de una secuencia de escape en las cadenas de documentación también. La macro de cadena `raw""` junto con la macro `@doc` se puede usar para evitar tener que escaparlos. Esto es útil cuando las cadenas de documentación incluyen ejemplos de código fuente de LaTeX o Julia que contienen interpolación:

````julia
@doc raw"""
```math
\LaTeX
```
"""
function f end
````

### Functions and Methods

```julia
"..."
function f end

"..."
f
```

Agrega la cadena de documentación `"..."` a la función `f`. La primera versión es la sintaxis preferida, sin embargo, ambas son equivalentes.

```julia
"..."
f(x) = x

"..."
function f(x)
    return x
end

"..."
f(x)
```

Agrega la cadena de documentación `"..."` al método `f(::Any)`.

```julia
"..."
f(x, y = 1) = x + y
```

Agrega la cadena de documentación `"..."` a dos `Métodos`, a saber, `f(::Any)` y `f(::Any, ::Any)`.

### Macros

```julia
"..."
macro m(x) end
```

Agrega la cadena de documentación `"..."` a la definición del macro `@m(::Any)`.

```julia
"..."
:(@m1)

"..."
macro m2 end
```

Agrega la cadena de documentación `"..."` a las macros llamadas `@m1` y `@m2`.

### Types

```
"..."
abstract type T1 end

"..."
mutable struct T2
    ...
end

"..."
struct T3
    ...
end
```

Agrega la cadena de documentación `"..."` a los tipos `T1`, `T2` y `T3`.

```
"..."
T1

"..."
T2

"..."
T3
```

Agrega la cadena de documentación `"..."` a los tipos `T1`, `T2` y `T3`. La versión anterior es la sintaxis preferida, sin embargo, ambas son equivalentes.

```julia
"..."
struct T
    "x"
    x
    "y"
    y

    @doc "Inner constructor"
    function T()
        new(...)
    end
end
```

Agrega la cadena de documentación `"..."` al tipo `T`, `"x"` al campo `T.x`, `"y"` al campo `T.y`, y `"Constructor interno"` al constructor interno `T()`. También aplicable a tipos `mutable struct`.

### Modules

```julia
"..."
module M end

module M

"..."
M

end
```

Agrega la cadena de documentación `"..."` al `Módulo` `M`. Agregar la cadena de documentación por encima del `Módulo` es la sintaxis preferida, sin embargo, ambas son equivalentes.

```julia
"..."
baremodule M
# ...
end

baremodule M

import Base: @doc

"..."
f(x) = x

end
```

Documentar un `baremodule` colocando una cadena de documentación encima de la expresión importa automáticamente `@doc` en el módulo. Estas importaciones deben hacerse manualmente cuando la expresión del módulo no está documentada.

### Global Variables

```julia
"..."
const a = 1

"..."
b = 2

"..."
global c = 3
```

Agrega la cadena de documentación `"..."` a los `Binding`s `a`, `b` y `c`.

Los `Binding`s se utilizan para almacenar una referencia a un `Symbol` particular en un `Module` sin almacenar el valor referenciado en sí.

!!! note
    Cuando una definición `const` se utiliza únicamente para definir un alias de otra definición, como es el caso de la función `div` y su alias `÷` en `Base`, no documentes el alias y en su lugar documenta la función real.

    Si el alias está documentado y no la definición real, entonces el sistema de documentación (`?` modo) no devolverá la cadena de documentación adjunta al alias cuando se busque la definición real.

    Por ejemplo, deberías escribir

    ```julia
    "..."
    f(x) = x + 1
    const alias = f
    ```

    en lugar de

    ```julia
    f(x) = x + 1
    "..."
    const alias = f
    ```


```julia
"..."
sym
```

Agrega la cadena de documentación `"..."` al valor asociado con `sym`. Sin embargo, se prefiere que `sym` esté documentado donde se define.

### Multiple Objects

```julia
"..."
a, b
```

Agrega la cadena de documentación `"..."` a `a` y `b`, cada uno de los cuales debe ser una expresión documentable. Esta sintaxis es equivalente a

```julia
"..."
a

"..."
b
```

Cualquier número de expresiones puede ser documentado junto de esta manera. Esta sintaxis puede ser útil cuando dos funciones están relacionadas, como las versiones no mutantes y mutantes `f` y `f!`.

### Macro-generated code

```julia
"..."
@m expression
```

Agrega la cadena de documentación `"..."` a la expresión generada al expandir `@m expression`. Esto permite que las expresiones decoradas con `@inline`, `@noinline`, `@generated` o cualquier otro macro sean documentadas de la misma manera que las expresiones no decoradas.

Los autores de macros deben tener en cuenta que solo las macros que generan una única expresión admitirán automáticamente las cadenas de documentación. Si una macro devuelve un bloque que contiene múltiples subexpresiones, entonces la subexpresión que debe ser documentada debe ser marcada utilizando la macro [`@__doc__`](@ref Core.@__doc__).

El macro [`@enum`](@ref) utiliza `@__doc__` para permitir la documentación de [`Enum`](@ref). Examinar su definición debería servir como un ejemplo de cómo usar `@__doc__` correctamente.

```@docs
Core.@__doc__
```
