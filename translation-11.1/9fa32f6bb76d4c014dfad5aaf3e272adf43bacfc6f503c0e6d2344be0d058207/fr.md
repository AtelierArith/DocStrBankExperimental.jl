```
prod!(r, A)
```

Multiplie les éléments de `A` sur les dimensions singleton de `r`, et écris les résultats dans `r`.

!!! avertissement
    Le comportement peut être inattendu lorsque tout argument modifié partage de la mémoire avec un autre argument.


# Exemples

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> prod!([1; 1], A)
2-element Vector{Int64}:
  2
 12

julia> prod!([1 1], A)
1×2 Matrix{Int64}:
 3  8
```
