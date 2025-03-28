```
spzeros([tipo,]m[,n])
```

Crea un vector disperso de longitud `m` o una matriz dispersa de tamaño `m x n`. Este arreglo disperso no contendrá ningún valor distinto de cero. No se asignará almacenamiento para valores distintos de cero durante la construcción. El tipo predeterminado es [`Float64`](@ref) si no se especifica.

# Ejemplos

```jldoctest
julia> spzeros(3, 3)
3×3 SparseMatrixCSC{Float64, Int64} con 0 entradas almacenadas:
  ⋅    ⋅    ⋅
  ⋅    ⋅    ⋅
  ⋅    ⋅    ⋅

julia> spzeros(Float32, 4)
4-element SparseVector{Float32, Int64} con 0 entradas almacenadas
```
