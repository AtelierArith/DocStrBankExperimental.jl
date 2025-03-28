```
union(s, itrs...)
∪(s, itrs...)
```

Construye un objeto que contenga todos los elementos distintos de todos los argumentos.

El primer argumento controla qué tipo de contenedor se devuelve. Si este es un array, mantiene el orden en el que los elementos aparecen por primera vez.

El Unicode `∪` se puede escribir escribiendo `\cup` y luego presionando tab en el REPL de Julia, y en muchos editores. Este es un operador infijo, permitiendo `s ∪ itr`.

Véase también [`unique`](@ref), [`intersect`](@ref), [`isdisjoint`](@ref), [`vcat`](@ref), [`Iterators.flatten`](@ref).

# Ejemplos

```jldoctest
julia> union([1, 2], [3])
3-element Vector{Int64}:
 1
 2
 3

julia> union([4 2 3 4 4], 1:3, 3.0)
4-element Vector{Float64}:
 4.0
 2.0
 3.0
 1.0

julia> (0, 0.0) ∪ (-0.0, NaN)
3-element Vector{Real}:
   0
  -0.0
 NaN

julia> union(Set([1, 2]), 2:3)
Set{Int64} with 3 elements:
  2
  3
  1
```
