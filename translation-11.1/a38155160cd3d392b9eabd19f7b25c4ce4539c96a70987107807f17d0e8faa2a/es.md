```
diagm(v::AbstractVector)
diagm(m::Integer, n::Integer, v::AbstractVector)
```

Construye una matriz con los elementos del vector como elementos diagonales. Por defecto, la matriz es cuadrada y su tamaño está dado por `length(v)`, pero se puede especificar un tamaño no cuadrado `m`×`n` pasando `m,n` como los primeros argumentos.

# Ejemplos

```jldoctest
julia> diagm([1,2,3])
3×3 Matrix{Int64}:
 1  0  0
 0  2  0
 0  0  3
```
