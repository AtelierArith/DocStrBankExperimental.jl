# Base.Cartesian

El módulo (no exportado) Cartesian proporciona macros que facilitan la escritura de algoritmos multidimensionales. Más a menudo, puedes escribir tales algoritmos con [straightforward techniques](https://julialang.org/blog/2016/02/iteration); sin embargo, hay algunos casos en los que `Base.Cartesian` sigue siendo útil o necesario.

## Principles of usage

Un ejemplo simple de uso es:

```julia
@nloops 3 i A begin
    s += @nref 3 A i
end
```

que genera el siguiente código:

```julia
for i_3 = axes(A, 3)
    for i_2 = axes(A, 2)
        for i_1 = axes(A, 1)
            s += A[i_1, i_2, i_3]
        end
    end
end
```

En general, Cartesian te permite escribir código genérico que contiene elementos repetitivos, como los bucles anidados en este ejemplo. Otras aplicaciones incluyen expresiones repetidas (por ejemplo, desenrollado de bucles) o crear llamadas a funciones con un número variable de argumentos sin usar el constructo "splat" (`i...`).

## Basic syntax

La sintaxis (básica) de `@nloops` es la siguiente:

  * El primer argumento debe ser un entero (*no* una variable) que especifique el número de bucles.
  * El segundo argumento es el prefijo de símbolo utilizado para la variable del iterador. Aquí usamos `i`, y se generaron las variables `i_1, i_2, i_3`.
  * El tercer argumento especifica el rango para cada variable de iterador. Si usas una variable (símbolo) aquí, se toma como `axes(A, dim)`. Más flexiblemente, puedes usar la sintaxis de expresión de función anónima descrita a continuación.
  * El último argumento es el cuerpo del bucle. Aquí, eso es lo que aparece entre `begin...end`.

Hay algunas características adicionales de `@nloops` descritas en el [reference section](@ref dev-cartesian-reference).

`@nref` sigue un patrón similar, generando `A[i_1,i_2,i_3]` a partir de `@nref 3 A i`. La práctica general es leer de izquierda a derecha, por lo que `@nloops` es `@nloops 3 i A expr` (como en `for i_2 = axes(A, 2)`, donde `i_2` está a la izquierda y el rango está a la derecha) mientras que `@nref` es `@nref 3 A i` (como en `A[i_1,i_2,i_3]`, donde el arreglo viene primero).

Si estás desarrollando código con Cartesian, puede que encuentres que depurar es más fácil cuando examinas el código generado, utilizando `@macroexpand`:

```@meta
DocTestSetup = quote
    import Base.Cartesian: @nref
end
```

```jldoctest
julia> @macroexpand @nref 2 A i
:(A[i_1, i_2])
```

```@meta
DocTestSetup = nothing
```

### Supplying the number of expressions

El primer argumento de ambos macros es el número de expresiones, que debe ser un entero. Cuando estás escribiendo una función que pretendes que funcione en múltiples dimensiones, esto puede no ser algo que desees codificar de forma rígida. El enfoque recomendado es usar una `@generated function`. Aquí hay un ejemplo:

```julia
@generated function mysum(A::Array{T,N}) where {T,N}
    quote
        s = zero(T)
        @nloops $N i A begin
            s += @nref $N A i
        end
        s
    end
end
```

Naturalmente, también puedes preparar expresiones o realizar cálculos antes del bloque `quote`.

### Anonymous-function expressions as macro arguments

Quizás la característica más poderosa en `Cartesian` es la capacidad de proporcionar expresiones de funciones anónimas que se evalúan en el momento del análisis. Consideremos un ejemplo simple:

```julia
@nexprs 2 j->(i_j = 1)
```

`@nexprs` genera `n` expresiones que siguen un patrón. Este código generaría las siguientes declaraciones:

```julia
i_1 = 1
i_2 = 1
```

En cada declaración generada, un `j` "aislado" (la variable de la función anónima) se reemplaza por valores en el rango `1:2`. Hablando en términos generales, Cartesian emplea una sintaxis similar a LaTeX. Esto te permite hacer matemáticas sobre el índice `j`. Aquí hay un ejemplo que calcula los pasos de un arreglo:

```julia
s_1 = 1
@nexprs 3 j->(s_{j+1} = s_j * size(A, j))
```

generar expresiones

```julia
s_1 = 1
s_2 = s_1 * size(A, 1)
s_3 = s_2 * size(A, 2)
s_4 = s_3 * size(A, 3)
```

Las expresiones de funciones anónimas tienen muchos usos en la práctica.

#### [Macro reference](@id dev-cartesian-reference)

```@docs
Base.Cartesian.@nloops
Base.Cartesian.@nref
Base.Cartesian.@nextract
Base.Cartesian.@nexprs
Base.Cartesian.@ncall
Base.Cartesian.@ncallkw
Base.Cartesian.@ntuple
Base.Cartesian.@nall
Base.Cartesian.@nany
Base.Cartesian.@nif
```
