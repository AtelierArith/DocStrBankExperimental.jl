```
axes(A)
```

Retourne le tuple des indices valides pour le tableau `A`.

Voir aussi : [`size`](@ref), [`keys`](@ref), [`eachindex`](@ref).

# Exemples

```jldoctest
julia> A = fill(1, (5,6,7));

julia> axes(A)
(Base.OneTo(5), Base.OneTo(6), Base.OneTo(7))
```
