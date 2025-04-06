```
splice!(a::Vector, index::Integer, [replacement]) -> item
```

Elimina el elemento en el índice dado y devuelve el elemento eliminado. Los elementos subsiguientes se desplazan a la izquierda para llenar el espacio resultante. Si se especifica, los valores de reemplazo de una colección ordenada se insertarán en lugar del elemento eliminado.

Véase también: [`replace`](@ref), [`delete!`](@ref), [`deleteat!`](@ref), [`pop!`](@ref), [`popat!`](@ref).

# Ejemplos

```jldoctest
julia> A = [6, 5, 4, 3, 2, 1]; splice!(A, 5)
2

julia> A
5-element Vector{Int64}:
 6
 5
 4
 3
 1

julia> splice!(A, 5, -1)
1

julia> A
5-element Vector{Int64}:
  6
  5
  4
  3
 -1

julia> splice!(A, 1, [-1, -2, -3])
6

julia> A
7-element Vector{Int64}:
 -1
 -2
 -3
  5
  4
  3
 -1
```

Para insertar `replacement` antes de un índice `n` sin eliminar ningún elemento, usa `splice!(collection, n:n-1, replacement)`.
