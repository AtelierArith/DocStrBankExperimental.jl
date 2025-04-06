```
hvcat(blocks_per_row::Union{Tuple{Vararg{Int}}, Int}, values...)
```

Concatenación horizontal y vertical en una sola llamada. Esta función se llama para la sintaxis de matrices en bloques. El primer argumento especifica el número de argumentos a concatenar en cada fila de bloques. Si el primer argumento es un solo entero `n`, entonces se asume que todas las filas de bloques tienen `n` columnas de bloques.

# Ejemplos

```jldoctest
julia> a, b, c, d, e, f = 1, 2, 3, 4, 5, 6
(1, 2, 3, 4, 5, 6)

julia> [a b c; d e f]
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> hvcat((3,3), a,b,c,d,e,f)
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> [a b; c d; e f]
3×2 Matrix{Int64}:
 1  2
 3  4
 5  6

julia> hvcat((2,2,2), a,b,c,d,e,f)
3×2 Matrix{Int64}:
 1  2
 3  4
 5  6
julia> hvcat((2,2,2), a,b,c,d,e,f) == hvcat(2, a,b,c,d,e,f)
true
```
