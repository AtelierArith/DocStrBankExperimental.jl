```
hvcat(blocks_per_row::Union{Tuple{Vararg{Int}}, Int}, values...)
```

Concaténation horizontale et verticale en un seul appel. Cette fonction est appelée pour la syntaxe de matrice de blocs. Le premier argument spécifie le nombre d'arguments à concaténer dans chaque ligne de blocs. Si le premier argument est un seul entier `n`, alors toutes les lignes de blocs sont supposées avoir `n` colonnes de blocs.

# Exemples

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
