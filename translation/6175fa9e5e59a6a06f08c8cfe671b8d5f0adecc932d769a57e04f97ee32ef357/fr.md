```
rot180(A, k)
```

Faire pivoter la matrice `A` de 180 degrés un nombre entier `k` de fois. Si `k` est pair, cela équivaut à une `copie`.

# Exemples

```jldoctest
julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> rot180(a,1)
2×2 Matrix{Int64}:
 4  3
 2  1

julia> rot180(a,2)
2×2 Matrix{Int64}:
 1  2
 3  4
```
