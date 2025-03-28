```
spdiagm(v::AbstractVector)
spdiagm(m::Integer, n::Integer, v::AbstractVector)
```

Construye una matriz dispersa con los elementos del vector como elementos diagonales. Por defecto (sin `m` y `n` dados), la matriz es cuadrada y su tamaño está dado por `length(v)`, pero se puede especificar un tamaño no cuadrado `m`×`n` pasando `m` y `n` como los primeros argumentos.

!!! compat "Julia 1.6"
    Estas funciones requieren al menos Julia 1.6.


# Ejemplos

```jldoctest
julia> spdiagm([1,2,3])
3×3 SparseMatrixCSC{Int64, Int64} con 3 entradas almacenadas:
 1  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  3

julia> spdiagm(sparse([1,0,3]))
3×3 SparseMatrixCSC{Int64, Int64} con 2 entradas almacenadas:
 1  ⋅  ⋅
 ⋅  ⋅  ⋅
 ⋅  ⋅  3
```
