```
diagm(kv::Pair{<:Integer,<:AbstractVector}...)
diagm(m::Integer, n::Integer, kv::Pair{<:Integer,<:AbstractVector}...)

Construye una matriz a partir de `Pair`s de diagonales y vectores. El vector `kv.second` se colocará en la diagonal `kv.first`. Por defecto, la matriz es cuadrada y su tamaño se infiere de `kv`, pero se puede especificar un tamaño no cuadrado `m`×`n` (rellenado con ceros según sea necesario) pasando `m,n` como los primeros argumentos. Para índices de diagonal repetidos `kv.first`, los valores en los vectores correspondientes `kv.second` se sumarán.

`diagm` construye una matriz completa; si deseas versiones que ahorren espacio con aritmética rápida, consulta [`Diagonal`](@ref), [`Bidiagonal`](@ref), [`Tridiagonal`](@ref) y [`SymTridiagonal`](@ref).

# Ejemplos

```

jldoctest julia> diagm(1 => [1,2,3]) 4×4 Matrix{Int64}:  0  1  0  0  0  0  2  0  0  0  0  3  0  0  0  0

julia> diagm(1 => [1,2,3], -1 => [4,5]) 4×4 Matrix{Int64}:  0  1  0  0  4  0  2  0  0  5  0  3  0  0  0  0

julia> diagm(1 => [1,2,3], 1 => [1,2,3]) 4×4 Matrix{Int64}:  0  2  0  0  0  0  4  0  0  0  0  6  0  0  0  0 ```
