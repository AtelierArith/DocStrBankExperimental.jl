```
rowvals(A::AbstractSparseMatrixCSC)
```

Devuelve un vector de los índices de fila de `A`. Cualquier modificación al vector devuelto también mutará `A`. Proporcionar acceso a cómo se almacenan internamente los índices de fila puede ser útil en conjunto con la iteración sobre valores no cero estructurales. Ver también [`nonzeros`](@ref) y [`nzrange`](@ref).

# Ejemplos

```jldoctest
julia> A = sparse(2I, 3, 3)
3×3 SparseMatrixCSC{Int64, Int64} con 3 entradas almacenadas:
 2  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  2

julia> rowvals(A)
Vector{Int64} de 3 elementos:
 1
 2
 3
```
