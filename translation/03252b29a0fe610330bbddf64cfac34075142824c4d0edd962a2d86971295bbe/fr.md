```
PermutedDimsArray(A, perm) -> B
```

Étant donné un AbstractArray `A`, créez une vue `B` telle que les dimensions semblent être permutées. Semblable à `permutedims`, sauf qu'aucune copie n'est effectuée (`B` partage le stockage avec `A`).

Voir aussi [`permutedims`](@ref), [`invperm`](@ref).

# Exemples

```jldoctest
julia> A = rand(3,5,4);

julia> B = PermutedDimsArray(A, (3,1,2));

julia> size(B)
(4, 3, 5)

julia> B[3,1,2] == A[1,2,3]
true
```
