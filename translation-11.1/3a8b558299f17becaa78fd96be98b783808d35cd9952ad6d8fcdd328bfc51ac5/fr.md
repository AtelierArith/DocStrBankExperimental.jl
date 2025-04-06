```
repeat(A::AbstractArray; inner=ntuple(Returns(1), ndims(A)), outer=ntuple(Returns(1), ndims(A)))
```

Construisez un tableau en répétant les entrées de `A`. L'élément i-ème de `inner` spécifie le nombre de fois que les entrées individuelles de la i-ème dimension de `A` doivent être répétées. L'élément i-ème de `outer` spécifie le nombre de fois qu'une tranche le long de la i-ème dimension de `A` doit être répétée. Si `inner` ou `outer` sont omis, aucune répétition n'est effectuée.

# Exemples

```jldoctest
julia> repeat(1:2, inner=2)
4-element Vector{Int64}:
 1
 1
 2
 2

julia> repeat(1:2, outer=2)
4-element Vector{Int64}:
 1
 2
 1
 2

julia> repeat([1 2; 3 4], inner=(2, 1), outer=(1, 3))
4×6 Matrix{Int64}:
 1  2  1  2  1  2
 1  2  1  2  1  2
 3  4  3  4  3  4
 3  4  3  4  3  4
```
