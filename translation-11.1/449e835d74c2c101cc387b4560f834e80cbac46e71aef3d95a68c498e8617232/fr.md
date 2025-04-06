```
nextind(A, i)
```

Renvoie l'index après `i` dans `A`. L'index retourné est souvent équivalent à `i + 1` pour un entier `i`. Cette fonction peut être utile pour du code générique.

!!! warning
    L'index retourné peut être hors limites. Envisagez d'utiliser [`checkbounds`](@ref).


Voir aussi : [`prevind`](@ref).

# Exemples

```jldoctest
julia> x = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> nextind(x, 1) # résultat valide
2

julia> nextind(x, 4) # résultat invalide
5

julia> nextind(x, CartesianIndex(1, 1)) # résultat valide
CartesianIndex(2, 1)

julia> nextind(x, CartesianIndex(2, 2)) # résultat invalide
CartesianIndex(1, 3)
```
