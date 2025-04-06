```
nonzeros(A)
```

Devuelve un vector de los valores no nulos estructurales en la matriz dispersa `A`. Esto incluye ceros que están almacenados explícitamente en la matriz dispersa. El vector devuelto apunta directamente al almacenamiento interno de no nulos de `A`, y cualquier modificación al vector devuelto también mutará `A`. Consulta [`rowvals`](@ref) y [`nzrange`](@ref).

# Ejemplos

```jldoctest
julia> A = sparse(2I, 3, 3)
3×3 SparseMatrixCSC{Int64, Int64} con 3 entradas almacenadas:
 2  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  2

julia> nonzeros(A)
3-element Vector{Int64}:
 2
 2
 2
```
