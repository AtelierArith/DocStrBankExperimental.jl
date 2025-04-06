```
permute!(v, p)
```

Permute le vecteur `v` sur place, selon la permutation `p`. Aucune vérification n'est effectuée pour vérifier que `p` est une permutation.

Pour retourner une nouvelle permutation, utilisez `v[p]`. Cela est généralement plus rapide que `permute!(v, p)` ; il est encore plus rapide d'écrire dans un tableau de sortie pré-alloué avec `u .= @view v[p]`. (Bien que `permute!` écrase `v` sur place, il nécessite en interne une certaine allocation pour garder une trace des éléments qui ont été déplacés.)

!!! warning
    Le comportement peut être inattendu lorsque tout argument muté partage de la mémoire avec un autre argument.


Voir aussi [`invpermute!`](@ref).

# Exemples

```jldoctest
julia> A = [1, 1, 3, 4];

julia> perm = [2, 4, 3, 1];

julia> permute!(A, perm);

julia> A
4-element Vector{Int64}:
 1
 4
 3
 1
```
