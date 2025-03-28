```
extrema!(r, A)
```

Calculez la valeur minimale et maximale de `A` sur les dimensions singleton de `r`, et écrivez les résultats dans `r`.

!!! avertissement
    Le comportement peut être inattendu lorsque tout argument modifié partage de la mémoire avec un autre argument.


!!! compat "Julia 1.8"
    Cette méthode nécessite Julia 1.8 ou une version ultérieure.


# Exemples

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> extrema!([(1, 1); (1, 1)], A)
2-element Vector{Tuple{Int64, Int64}}:
 (1, 2)
 (3, 4)

julia> extrema!([(1, 1);; (1, 1)], A)
1×2 Matrix{Tuple{Int64, Int64}}:
 (1, 3)  (2, 4)
```
