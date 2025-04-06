```
spdiagm(kv::Pair{<:Integer,<:AbstractVector}...)
spdiagm(m::Integer, n::Integer, kv::Pair{<:Integer,<:AbstractVector}...)

Construye una matriz diagonal dispersa a partir de `Pair`s de vectores y diagonales. Cada vector `kv.second` se colocará en la diagonal `kv.first`. Por defecto, la matriz es cuadrada y su tamaño se infiere de `kv`, pero se puede especificar un tamaño no cuadrado `m`×`n` (rellenado con ceros según sea necesario) pasando `m,n` como los primeros argumentos.

# Ejemplos

```

jldoctest julia> spdiagm(-1 => [1,2,3,4], 1 => [4,3,2,1]) 5×5 SparseMatrixCSC{Int64, Int64} con 8 entradas almacenadas:  ⋅  4  ⋅  ⋅  ⋅  1  ⋅  3  ⋅  ⋅  ⋅  2  ⋅  2  ⋅  ⋅  ⋅  3  ⋅  1  ⋅  ⋅  ⋅  4  ⋅

```

```
