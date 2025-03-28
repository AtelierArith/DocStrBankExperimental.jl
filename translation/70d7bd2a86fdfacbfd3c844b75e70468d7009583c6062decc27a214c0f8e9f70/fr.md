```
prevind(A, i)
```

Retourne l'index avant `i` dans `A`. L'index retourné est souvent équivalent à `i - 1` pour un entier `i`. Cette fonction peut être utile pour du code générique.

!!! warning
    L'index retourné peut être hors limites. Envisagez d'utiliser [`checkbounds`](@ref).


Voir aussi : [`nextind`](@ref).

# Exemples

```jldoctest
julia> x = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> prevind(x, 4) # résultat valide
3

julia> prevind(x, 1) # résultat invalide
0

julia> prevind(x, CartesianIndex(2, 2)) # résultat valide
CartesianIndex(1, 2)

julia> prevind(x, CartesianIndex(1, 1)) # résultat invalide
CartesianIndex(2, 0)
```
