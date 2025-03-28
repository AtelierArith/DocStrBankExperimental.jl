```
hvcat(blocks_per_row::Union{Tuple{Vararg{Int}}, Int}, values...)
```

Horizontale und vertikale Verkettung in einem Aufruf. Diese Funktion wird für die Blockmatrix-Syntax aufgerufen. Das erste Argument gibt die Anzahl der Argumente an, die in jeder Blockreihe verkettet werden sollen. Wenn das erste Argument eine einzelne Ganzzahl `n` ist, wird angenommen, dass alle Blockreihen `n` Blockspalten haben.

# Beispiele

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
