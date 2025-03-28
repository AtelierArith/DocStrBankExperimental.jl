```
tuple(xs...)
```

Konstruiere ein Tupel der gegebenen Objekte.

Siehe auch [`Tuple`](@ref), [`ntuple`](@ref), [`NamedTuple`](@ref).

# Beispiele

```jldoctest
julia> tuple(1, 'b', pi)
(1, 'b', π)

julia> ans === (1, 'b', π)
true

julia> Tuple(Real[1, 2, pi])  # nimmt eine Sammlung
(1, 2, π)
```
