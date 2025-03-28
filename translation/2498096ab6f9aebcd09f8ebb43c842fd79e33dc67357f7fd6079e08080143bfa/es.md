# Sorting and Related Functions

Julia tiene una API extensa y flexible para ordenar e interactuar con arreglos de valores ya ordenados. Por defecto, Julia elige algoritmos razonables y ordena en orden ascendente:

```jldoctest
julia> sort([2,3,1])
3-element Vector{Int64}:
 1
 2
 3
```

También puedes ordenar en orden inverso:

```jldoctest
julia> sort([2,3,1], rev=true)
3-element Vector{Int64}:
 3
 2
 1
```

`sort` construye una copia ordenada dejando su entrada sin cambios. Usa la versión "bang" de la función de ordenamiento para mutar un array existente:

```jldoctest
julia> a = [2,3,1];

julia> sort!(a);

julia> a
3-element Vector{Int64}:
 1
 2
 3
```

En lugar de ordenar directamente un arreglo, puedes calcular una permutación de los índices del arreglo que coloca el arreglo en orden ordenado:

```julia-repl
julia> v = randn(5)
5-element Array{Float64,1}:
  0.297288
  0.382396
 -0.597634
 -0.0104452
 -0.839027

julia> p = sortperm(v)
5-element Array{Int64,1}:
 5
 3
 4
 1
 2

julia> v[p]
5-element Array{Float64,1}:
 -0.839027
 -0.597634
 -0.0104452
  0.297288
  0.382396
```

Los arreglos se pueden ordenar de acuerdo con una transformación arbitraria de sus valores:

```julia-repl
julia> sort(v, by=abs)
5-element Array{Float64,1}:
 -0.0104452
  0.297288
  0.382396
 -0.597634
 -0.839027
```

O en orden inverso por una transformación:

```julia-repl
julia> sort(v, by=abs, rev=true)
5-element Array{Float64,1}:
 -0.839027
 -0.597634
  0.382396
  0.297288
 -0.0104452
```

Si es necesario, se puede elegir el algoritmo de ordenamiento:

```julia-repl
julia> sort(v, alg=InsertionSort)
5-element Array{Float64,1}:
 -0.839027
 -0.597634
 -0.0104452
  0.297288
  0.382396
```

Todas las funciones relacionadas con la ordenación y el orden dependen de una relación de "menor que" que define un [strict weak order](https://en.wikipedia.org/wiki/Weak_ordering#Strict_weak_orderings) sobre los valores a manipular. La función `isless` se invoca por defecto, pero la relación se puede especificar a través de la palabra clave `lt`, una función que toma dos elementos de un arreglo y devuelve `true` si y solo si el primer argumento es "menor que" el segundo. Consulte [`sort!`](@ref) y [Alternate Orderings](@ref) para más información.

## Sorting Functions

```@docs
Base.sort!
Base.sort
Base.sortperm
Base.InsertionSort
Base.MergeSort
Base.QuickSort
Base.PartialQuickSort
Base.Sort.sortperm!
Base.Sort.sortslices
```

## Order-Related Functions

```@docs
Base.issorted
Base.Sort.searchsorted
Base.Sort.searchsortedfirst
Base.Sort.searchsortedlast
Base.Sort.insorted
Base.Sort.partialsort!
Base.Sort.partialsort
Base.Sort.partialsortperm
Base.Sort.partialsortperm!
```

## Sorting Algorithms

Actualmente hay cuatro algoritmos de ordenamiento disponibles públicamente en Julia base:

  * [`InsertionSort`](@ref)
  * [`QuickSort`](@ref)
  * [`PartialQuickSort(k)`](@ref)
  * [`MergeSort`](@ref)

Por defecto, la familia de funciones `sort` utiliza algoritmos de ordenamiento estables que son rápidos en la mayoría de las entradas. La elección exacta del algoritmo es un detalle de implementación para permitir futuras mejoras en el rendimiento. Actualmente, se utiliza un híbrido de `RadixSort`, `ScratchQuickSort`, `InsertionSort` y `CountingSort` basado en el tipo de entrada, tamaño y composición. Los detalles de implementación están sujetos a cambios, pero actualmente están disponibles en la ayuda extendida de `??Base.DEFAULT_STABLE` y en las cadenas de documentación de los algoritmos de ordenamiento internos que se enumeran allí.

Puedes especificar explícitamente tu algoritmo preferido con la palabra clave `alg` (por ejemplo, `sort!(v, alg=PartialQuickSort(10:20))`) o reconfigurar el algoritmo de ordenamiento predeterminado para tipos personalizados añadiendo un método especializado a la función `Base.Sort.defalg`. Por ejemplo, [InlineStrings.jl](https://github.com/JuliaStrings/InlineStrings.jl/blob/v1.3.2/src/InlineStrings.jl#L903) define el siguiente método:

```julia
Base.Sort.defalg(::AbstractArray{<:Union{SmallInlineStrings, Missing}}) = InlineStringSort
```

!!! compat "Julia 1.9"
    El algoritmo de ordenamiento predeterminado (devuelto por `Base.Sort.defalg`) está garantizado como estable desde Julia 1.9. Las versiones anteriores tenían casos extremos inestables al ordenar arreglos numéricos.


## Alternate Orderings

Por defecto, `sort`, `searchsorted` y funciones relacionadas utilizan [`isless`](@ref) para comparar dos elementos con el fin de determinar cuál debe ir primero. El tipo abstracto [`Base.Order.Ordering`](@ref) proporciona un mecanismo para definir ordenamientos alternativos en el mismo conjunto de elementos: al llamar a una función de ordenamiento como `sort!`, se puede proporcionar una instancia de `Ordering` con el argumento de palabra clave `order`.

Las instancias de `Ordering` definen un orden a través de la función [`Base.Order.lt`](@ref), que funciona como una generalización de `isless`. El comportamiento de esta función en `Ordering`s personalizados debe satisfacer todas las condiciones de un [strict weak order](https://en.wikipedia.org/wiki/Weak_ordering#Strict_weak_orderings). Consulte [`sort!`](@ref) para obtener detalles y ejemplos de funciones `lt` válidas e inválidas.

```@docs
Base.Order.Ordering
Base.Order.lt
Base.Order.ord
Base.Order.Forward
Base.Order.ReverseOrdering
Base.Order.Reverse
Base.Order.By
Base.Order.Lt
Base.Order.Perm
```
