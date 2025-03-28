```
intersect(s, itrs...)
∩(s, itrs...)
```

Construye el conjunto que contiene aquellos elementos que aparecen en todos los argumentos.

El primer argumento controla qué tipo de contenedor se devuelve. Si este es un array, mantiene el orden en el que los elementos aparecen por primera vez.

El Unicode `∩` se puede escribir escribiendo `\cap` y luego presionando tab en el REPL de Julia, y en muchos editores. Este es un operador infijo, permitiendo `s ∩ itr`.

Véase también [`setdiff`](@ref), [`isdisjoint`](@ref), [`issubset`](@ref Base.issubset), [`issetequal`](@ref).

!!! compat "Julia 1.8"
    A partir de Julia 1.8, intersect devuelve un resultado con el eltype de los eltypes promovidos de los dos inputs.


# Ejemplos

```jldoctest
julia> intersect([1, 2, 3], [3, 4, 5])
1-element Vector{Int64}:
 3

julia> intersect([1, 4, 4, 5, 6], [6, 4, 6, 7, 8])
2-element Vector{Int64}:
 4
 6

julia> intersect(1:16, 7:99)
7:16

julia> (0, 0.0) ∩ (-0.0, 0)
1-element Vector{Real}:
 0

julia> intersect(Set([1, 2]), BitSet([2, 3]), 1.0:10.0)
Set{Float64} with 1 element:
  2.0
```
