```
parent(A)
```

Devuelve el objeto padre subyacente de la vista. Este padre de objetos de tipos `SubArray`, `SubString`, `ReshapedArray` o `LinearAlgebra.Transpose` es lo que se pasó como argumento a `view`, `reshape`, `transpose`, etc. durante la creación del objeto. Si la entrada no es un objeto envuelto, devuelve la entrada misma. Si la entrada está envuelta múltiples veces, solo se eliminará el envoltorio más externo.

# Ejemplos

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> V = view(A, 1:2, :)
2×2 view(::Matrix{Int64}, 1:2, :) con el tipo eltype Int64:
 1  2
 3  4

julia> parent(V)
2×2 Matrix{Int64}:
 1  2
 3  4
```
