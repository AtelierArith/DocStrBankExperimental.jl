```
count([f=identity,] A::AbstractArray; dims=:)
```

Comptez le nombre d'éléments dans `A` pour lesquels `f` renvoie `true` sur les dimensions données.

!!! compat "Julia 1.5"
    Le mot-clé `dims` a été ajouté dans Julia 1.5.


!!! compat "Julia 1.6"
    Le mot-clé `init` a été ajouté dans Julia 1.6.


# Exemples

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> count(<=(2), A, dims=1)
1×2 Matrix{Int64}:
 1  1

julia> count(<=(2), A, dims=2)
2×1 Matrix{Int64}:
 2
 0
```
