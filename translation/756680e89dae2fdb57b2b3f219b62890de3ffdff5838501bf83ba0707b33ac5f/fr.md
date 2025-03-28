```
ndims(A::AbstractArray) -> Integer
```

Retourne le nombre de dimensions de `A`.

Voir aussi : [`size`](@ref), [`axes`](@ref).

# Exemples

```jldoctest
julia> A = fill(1, (3,4,5));

julia> ndims(A)
3
```
