```
repeat(A::AbstractArray, counts::Integer...)
```

Construit un tableau en répétant le tableau `A` un nombre donné de fois dans chaque dimension, spécifié par `counts`.

Voir aussi : [`fill`](@ref), [`Iterators.repeated`](@ref), [`Iterators.cycle`](@ref).

# Exemples

```jldoctest
julia> repeat([1, 2, 3], 2)
6-element Vector{Int64}:
 1
 2
 3
 1
 2
 3

julia> repeat([1, 2, 3], 2, 3)
6×3 Matrix{Int64}:
 1  1  1
 2  2  2
 3  3  3
 1  1  1
 2  2  2
 3  3  3
```
