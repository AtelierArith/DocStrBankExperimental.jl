```
any!(r, A)
```

Testez si des valeurs dans `A` le long des dimensions singleton de `r` sont `true`, et écrivez les résultats dans `r`.

!!! warning
    Le comportement peut être inattendu lorsque tout argument modifié partage de la mémoire avec un autre argument.


# Exemples

```jldoctest
julia> A = [true false; true false]
2×2 Matrix{Bool}:
 1  0
 1  0

julia> any!([1; 1], A)
2-element Vector{Int64}:
 1
 1

julia> any!([1 1], A)
1×2 Matrix{Int64}:
 1  0
```
