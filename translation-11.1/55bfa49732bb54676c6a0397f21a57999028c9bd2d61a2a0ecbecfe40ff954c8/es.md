```
splice!(a::Vector, indices, [replacement]) -> items
```

Elimina elementos en los índices especificados y devuelve una colección que contiene los elementos eliminados. Los elementos subsiguientes se desplazan a la izquierda para llenar los huecos resultantes. Si se especifica, los valores de reemplazo de una colección ordenada se insertarán en lugar de los elementos eliminados; en este caso, `indices` debe ser un `AbstractUnitRange`.

Para insertar `replacement` antes de un índice `n` sin eliminar ningún elemento, usa `splice!(collection, n:n-1, replacement)`.

!!! warning
    El comportamiento puede ser inesperado cuando cualquier argumento mutado comparte memoria con cualquier otro argumento.


!!! compat "Julia 1.5"
    Antes de Julia 1.5, `indices` siempre debe ser un `UnitRange`.


!!! compat "Julia 1.8"
    Antes de Julia 1.8, `indices` debe ser un `UnitRange` si se insertan valores de reemplazo.


# Ejemplos

```jldoctest
julia> A = [-1, -2, -3, 5, 4, 3, -1]; splice!(A, 4:3, 2)
Int64[]

julia> A
8-element Vector{Int64}:
 -1
 -2
 -3
  2
  5
  4
  3
 -1
```
