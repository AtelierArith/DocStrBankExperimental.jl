# Julia Functions

Este documento explicará cómo funcionan las funciones, las definiciones de métodos y las tablas de métodos.

## Method Tables

Cada función en Julia es una función genérica. Una función genérica es conceptualmente una sola función, pero consiste en muchas definiciones, o métodos. Los métodos de una función genérica se almacenan en una tabla de métodos. Las tablas de métodos (tipo `MethodTable`) están asociadas con `TypeName`s. Un `TypeName` describe una familia de tipos parametrizados. Por ejemplo, `Complex{Float32}` y `Complex{Float64}` comparten el mismo objeto de nombre de tipo `Complex`.

Todos los objetos en Julia son potencialmente llamables, porque cada objeto tiene un tipo, que a su vez tiene un `TypeName`.

## [Function calls](@id Function-calls)

Dada la llamada `f(x, y)`, se realizan los siguientes pasos: primero, se accede a la tabla de métodos a utilizar como `typeof(f).name.mt`. En segundo lugar, se forma un tipo de tupla de argumentos, `Tuple{typeof(f), typeof(x), typeof(y)}`. Tenga en cuenta que el tipo de la función en sí es el primer elemento. Esto se debe a que el tipo puede tener parámetros y, por lo tanto, necesita participar en la dispatch. Este tipo de tupla se busca en la tabla de métodos.

Este proceso de despacho es realizado por `jl_apply_generic`, que toma dos argumentos: un puntero a un arreglo de los valores `f`, `x` y `y`, y el número de valores (en este caso 3).

A lo largo del sistema, hay dos tipos de APIs que manejan funciones y listas de argumentos: aquellas que aceptan la función y los argumentos por separado, y aquellas que aceptan una única estructura de argumento. En el primer tipo de API, la parte de "argumentos" *no* contiene información sobre la función, ya que esta se pasa por separado. En el segundo tipo de API, la función es el primer elemento de la estructura de argumento.

Por ejemplo, la siguiente función para realizar una llamada acepta solo un puntero `args`, por lo que el primer elemento del arreglo args será la función a llamar:

```c
jl_value_t *jl_apply(jl_value_t **args, uint32_t nargs)
```

Este punto de entrada para la misma funcionalidad acepta la función por separado, por lo que el array `args` no contiene la función:

```c
jl_value_t *jl_call(jl_function_t *f, jl_value_t **args, int32_t nargs);
```

## Adding methods

Dado el proceso de despacho anterior, conceptualmente todo lo que se necesita para agregar un nuevo método es (1) un tipo de tupla y (2) código para el cuerpo del método. `jl_method_def` implementa esta operación. Se llama a `jl_method_table_for` para extraer la tabla de métodos relevante de lo que sería el tipo del primer argumento. Esto es mucho más complicado que el procedimiento correspondiente durante el despacho, ya que el tipo de tupla de argumentos podría ser abstracto. Por ejemplo, podemos definir:

```julia
(::Union{Foo{Int},Foo{Int8}})(x) = 0
```

lo que funciona ya que todos los métodos de coincidencia posibles pertenecerían a la misma tabla de métodos.

## Creating generic functions

Dado que cada objeto es invocable, no se necesita nada especial para crear una función genérica. Por lo tanto, `jl_new_generic_function` simplemente crea un nuevo subtipo singleton (de 0 tamaño) de `Function` y devuelve su instancia. Una función puede tener un "nombre de visualización" mnemotécnico que se utiliza en la información de depuración y al imprimir objetos. Por ejemplo, el nombre de `Base.sin` es `sin`. Por convención, el nombre del *tipo* creado es el mismo que el nombre de la función, con un `#` precedido. Así que `typeof(sin)` es `Base.#sin`.

## Closures

Un cierre es simplemente un objeto llamable con nombres de campo que corresponden a las variables capturadas. Por ejemplo, el siguiente código:

```julia
function adder(x)
    return y->x+y
end
```

se reduce a (aproximadamente):

```julia
struct ##1{T}
    x::T
end

(_::##1)(y) = _.x + y

function adder(x)
    return ##1(x)
end
```

## Constructors

Una llamada a un constructor es simplemente una llamada a un tipo. La tabla de métodos para `Type` contiene todas las definiciones de constructores. Todos los subtipos de `Type` (`Type`, `UnionAll`, `Union` y `DataType`) comparten actualmente una tabla de métodos a través de un arreglo especial.

## Builtins

Las funciones "builtin", definidas en el módulo `Core`, son:

```@eval
function lines(words)
    io = IOBuffer()
    n = 0
    for w in words
        if n+length(w) > 80
            print(io, '\n', w)
            n = length(w)
        elseif n == 0
            print(io, w);
            n += length(w)
        else
            print(io, ' ', w);
            n += length(w)+1
        end
    end
    String(take!(io))
end
import Markdown
[string(n) for n in names(Core;all=true)
    if getfield(Core,n) isa Core.Builtin && nameof(getfield(Core,n)) === n] |>
    lines |>
    s ->  "```\n$s\n```" |>
    Markdown.parse
```

Estos son todos objetos singleton cuyos tipos son subtipos de `Builtin`, que es un subtipo de `Function`. Su propósito es exponer puntos de entrada en el tiempo de ejecución que utilizan la convención de llamada "jlcall":

```c
jl_value_t *(jl_value_t*, jl_value_t**, uint32_t)
```

Los métodos de las tablas de builtins están vacíos. En su lugar, tienen una única entrada de caché de método que captura todo (`Tuple{Vararg{Any}}`) cuyo puntero fptr de jlcall apunta a la función correcta. Esto es una especie de truco, pero funciona razonablemente bien.

## Keyword arguments

Los argumentos de palabra clave funcionan al agregar métodos a la función kwcall. Esta función es generalmente el "ordenador de argumentos de palabra clave" o "ordenador de palabras clave", que luego llama al cuerpo interno de la función (definido anónimamente). Cada definición en la función kwsorter tiene los mismos argumentos que alguna definición en la tabla de métodos normal, excepto con un único argumento `NamedTuple` precedido, que proporciona los nombres y valores de los argumentos de palabra clave pasados. La tarea del kwsorter es mover los argumentos de palabra clave a sus posiciones canónicas basadas en el nombre, además de evaluar y sustituir cualquier expresión de valor predeterminado necesaria. El resultado es una lista normal de argumentos posicionales, que luego se pasa a otra función generada por el compilador.

La forma más fácil de entender el proceso es observar cómo se reduce una definición de método con argumentos de palabra clave. El código:

```julia
function circle(center, radius; color = black, fill::Bool = true, options...)
    # draw
end
```

en realidad produce *tres* definiciones de método. La primera es una función que acepta todos los argumentos (incluidos los argumentos de palabra clave) como argumentos posicionales, e incluye el código para el cuerpo del método. Tiene un nombre generado automáticamente:

```julia
function #circle#1(color, fill::Bool, options, circle, center, radius)
    # draw
end
```

El segundo método es una definición ordinaria para la función original `circle`, que maneja el caso en el que no se pasan argumentos de palabra clave:

```julia
function circle(center, radius)
    #circle#1(black, true, pairs(NamedTuple()), circle, center, radius)
end
```

Esto simplemente despacha al primer método, pasando los valores predeterminados. `pairs` se aplica a la tupla nombrada de argumentos restantes para proporcionar iteración de pares clave-valor. Tenga en cuenta que si el método no acepta argumentos de palabra clave restantes, entonces este argumento está ausente.

Finalmente, hay la definición de kwsorter:

```
function (::Core.kwftype(typeof(circle)))(kws, circle, center, radius)
    if haskey(kws, :color)
        color = kws.color
    else
        color = black
    end
    # etc.

    # put remaining kwargs in `options`
    options = structdiff(kws, NamedTuple{(:color, :fill)})

    # if the method doesn't accept rest keywords, throw an error
    # unless `options` is empty

    #circle#1(color, fill, pairs(options), circle, center, radius)
end
```

La función `Core.kwftype(t)` crea el campo `t.name.mt.kwsorter` (si aún no se ha creado) y devuelve el tipo de esa función.

Este diseño tiene la característica de que los sitios de llamada que no utilizan argumentos de palabra clave no requieren un manejo especial; todo funciona como si no fueran parte del lenguaje en absoluto. Los sitios de llamada que utilizan argumentos de palabra clave se envían directamente al kwsorter de la función llamada. Por ejemplo, la llamada:

```julia
circle((0, 0), 1.0, color = red; other...)
```

se reduce a:

```julia
kwcall(merge((color = red,), other), circle, (0, 0), 1.0)
```

`kwcall` (también en `Core`) denota una firma y despacho de kwcall. La operación de splatting de palabras clave (escrita como `other...`) llama a la función `merge` de tuplas nombradas. Esta función descompone aún más cada *elemento* de `other`, esperando que cada uno contenga dos valores (un símbolo y un valor). Naturalmente, una implementación más eficiente está disponible si todos los argumentos splatted son tuplas nombradas. Observe que la función original `circle` se pasa a través, para manejar cierres.

## [Compiler efficiency issues](@id compiler-efficiency-issues)

Generar un nuevo tipo para cada función tiene consecuencias potencialmente graves para el uso de recursos del compilador cuando se combina con el diseño de Julia de "especializar en todos los argumentos por defecto". De hecho, la implementación inicial de este diseño sufrió de tiempos de construcción y prueba mucho más largos, mayor uso de memoria y una imagen del sistema casi 2x más grande que la base. En una implementación ingenua, el problema es lo suficientemente grave como para hacer que el sistema sea casi inutilizable. Se necesitaron varias optimizaciones significativas para hacer que el diseño fuera práctico.

El primer problema es la especialización excesiva de funciones para diferentes valores de argumentos que son funciones. Muchas funciones simplemente "transmiten" un argumento a otro lugar, por ejemplo, a otra función o a una ubicación de almacenamiento. Tales funciones no necesitan ser especializadas para cada cierre que podría ser pasado. Afortunadamente, este caso es fácil de distinguir simplemente considerando si una función *llama* a uno de sus argumentos (es decir, el argumento aparece en "posición de cabeza" en algún lugar). Las funciones de orden superior críticas para el rendimiento, como `map`, ciertamente llaman a su función argumento y, por lo tanto, seguirán siendo especializadas como se espera. Esta optimización se implementa registrando qué argumentos se llaman durante la pasada de `analyze-variables` en el front end. Cuando `cache_method` ve un argumento en la jerarquía de tipos `Function` pasado a un slot declarado como `Any` o `Function`, se comporta como si se hubiera aplicado la anotación `@nospecialize`. Esta heurística parece ser extremadamente efectiva en la práctica.

El siguiente problema concierne a la estructura de las tablas hash de caché de métodos. Los estudios empíricos muestran que la gran mayoría de las llamadas despachadas dinámicamente involucran uno o dos argumentos. A su vez, muchos de estos casos se pueden resolver considerando solo el primer argumento. (Aparte: los defensores del despacho único no se sorprenderían en absoluto por esto. Sin embargo, este argumento significa "el despacho múltiple es fácil de optimizar en la práctica", y que por lo tanto deberíamos usarlo, *no* "deberíamos usar el despacho único"!) Así que la caché de métodos utiliza el tipo del primer argumento como su clave principal. Sin embargo, esto corresponde al *segundo* elemento del tipo de tupla para una llamada a función (el primer elemento siendo el tipo de la función en sí). Típicamente, la variación de tipo en la posición de cabeza es extremadamente baja; de hecho, la mayoría de las funciones pertenecen a tipos singleton sin parámetros. Sin embargo, este no es el caso para los constructores, donde una única tabla de métodos contiene constructores para cada tipo. Por lo tanto, la tabla de métodos `Type` se trata de manera especial para usar el *primer* elemento del tipo de tupla en lugar del segundo.

El front end genera declaraciones de tipo para todos los cierres. Inicialmente, esto se implementó generando declaraciones de tipo normales. Sin embargo, esto produjo un número extremadamente grande de constructores, todos los cuales eran triviales (simplemente pasando todos los argumentos a [`new`](@ref)). Dado que los métodos están parcialmente ordenados, insertar todos estos métodos es O(n²), además de que simplemente hay demasiados para mantener. Esto se optimizó generando expresiones `struct_type` directamente (eludiendo la generación de constructores predeterminados) y utilizando `new` directamente para crear instancias de cierre. No es lo más bonito del mundo, pero haces lo que tienes que hacer.

El siguiente problema fue el macro `@test`, que generaba un cierre de 0 argumentos para cada caso de prueba. Esto no es realmente necesario, ya que cada caso de prueba se ejecuta simplemente una vez en su lugar. Por lo tanto, `@test` se modificó para expandirse a un bloque try-catch que registra el resultado de la prueba (verdadero, falso o excepción levantada) y llama al manejador de la suite de pruebas sobre ello.
