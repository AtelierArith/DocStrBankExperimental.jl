```
dropdims(A; dims)
```

Renvoie un tableau avec les mêmes données que `A`, mais avec les dimensions spécifiées par `dims` supprimées. `size(A,d)` doit être égal à 1 pour chaque `d` dans `dims`, et les dimensions répétées ou les nombres en dehors de `1:ndims(A)` sont interdits.

Le résultat partage les mêmes données sous-jacentes que `A`, de sorte que le résultat est mutable si et seulement si `A` est mutable, et que la modification des éléments de l'un altère les valeurs de l'autre.

Voir aussi : [`reshape`](@ref), [`vec`](@ref).

# Exemples

```jldoctest
julia> a = reshape(Vector(1:4),(2,2,1,1))
2×2×1×1 Array{Int64, 4}:
[:, :, 1, 1] =
 1  3
 2  4

julia> b = dropdims(a; dims=3)
2×2×1 Array{Int64, 3}:
[:, :, 1] =
 1  3
 2  4

julia> b[1,1,1] = 5; a
2×2×1×1 Array{Int64, 4}:
[:, :, 1, 1] =
 5  3
 2  4
```
