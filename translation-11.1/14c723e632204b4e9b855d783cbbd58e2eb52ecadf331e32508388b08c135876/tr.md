```
tuple(xs...)
```

Verilen nesnelerin bir demetini oluşturur.

Ayrıca bkz. [`Tuple`](@ref), [`ntuple`](@ref), [`NamedTuple`](@ref).

# Örnekler

```jldoctest
julia> tuple(1, 'b', pi)
(1, 'b', π)

julia> ans === (1, 'b', π)
true

julia> Tuple(Real[1, 2, pi])  # bir koleksiyon alır
(1, 2, π)
```
