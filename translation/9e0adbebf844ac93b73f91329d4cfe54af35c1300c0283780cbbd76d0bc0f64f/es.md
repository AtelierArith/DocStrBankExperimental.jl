```
findnz(A::SparseMatrixCSC)
```

Devuelve una tupla `(I, J, V)` donde `I` y `J` son los índices de fila y columna de los valores almacenados ("estructuralmente no cero") en la matriz dispersa `A`, y `V` es un vector de los valores.

# Ejemplos

```jldoctest
julia> A = sparse([1 2 0; 0 0 3; 0 4 0])
3×3 SparseMatrixCSC{Int64, Int64} con 4 entradas almacenadas:
 1  2  ⋅
 ⋅  ⋅  3
 ⋅  4  ⋅

julia> findnz(A)
([1, 1, 3, 2], [1, 2, 2, 3], [1, 2, 4, 3])
```
