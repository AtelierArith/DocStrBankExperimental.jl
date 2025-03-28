```
sum!(r, A)
```

Somme des éléments de `A` sur les dimensions singleton de `r`, et écrivez les résultats dans `r`.

!!! warning
    Le comportement peut être inattendu lorsque tout argument modifié partage de la mémoire avec un autre argument.


# Exemples

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> sum!([1; 1], A)
2-element Vector{Int64}:
 3
 7

julia> sum!([1 1], A)
1×2 Matrix{Int64}:
 4  6
```
