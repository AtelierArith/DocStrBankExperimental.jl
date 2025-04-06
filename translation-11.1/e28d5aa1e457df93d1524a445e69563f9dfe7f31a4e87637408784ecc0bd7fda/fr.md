```
invpermute!(v, p)
```

Comme [`permute!`](@ref), mais l'inverse de la permutation donnée est appliqué.

Notez que si vous avez un tableau de sortie préalloué (par exemple `u = similar(v)`), il est plus rapide d'utiliser `u[p] = v`. (`invpermute!` alloue en interne une copie des données.)

!!! avertissement
    Le comportement peut être inattendu lorsque tout argument muté partage de la mémoire avec un autre argument.


# Exemples

```jldoctest
julia> A = [1, 1, 3, 4];

julia> perm = [2, 4, 3, 1];

julia> invpermute!(A, perm);

julia> A
4-element Vector{Int64}:
 4
 1
 3
 1
```
