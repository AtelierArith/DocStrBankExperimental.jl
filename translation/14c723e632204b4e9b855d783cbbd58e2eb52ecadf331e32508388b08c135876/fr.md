```
tuple(xs...)
```

Construit un tuple des objets donnés.

Voir aussi [`Tuple`](@ref), [`ntuple`](@ref), [`NamedTuple`](@ref).

# Exemples

```jldoctest
julia> tuple(1, 'b', pi)
(1, 'b', π)

julia> ans === (1, 'b', π)
true

julia> Tuple(Real[1, 2, pi])  # prend une collection
(1, 2, π)
```
