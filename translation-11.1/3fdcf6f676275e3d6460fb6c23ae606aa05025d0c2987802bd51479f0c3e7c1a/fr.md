```
rotl90(A, k)
```

Faites pivoter la matrice `A` de 90 degrés dans le sens antihoraire un nombre entier `k` de fois. Si `k` est un multiple de quatre (y compris zéro), cela équivaut à une `copie`.

# Exemples

```jldoctest
julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> rotl90(a,1)
2×2 Matrix{Int64}:
 2  4
 1  3

julia> rotl90(a,2)
2×2 Matrix{Int64}:
 4  3
 2  1

julia> rotl90(a,3)
2×2 Matrix{Int64}:
 3  1
 4  2

julia> rotl90(a,4)
2×2 Matrix{Int64}:
 1  2
 3  4
```
