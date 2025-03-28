```
NTuple{N, T}
```

Eine kompakte Möglichkeit, den Typ für ein Tupel der Länge `N` darzustellen, bei dem alle Elemente vom Typ `T` sind.

# Beispiele

```jldoctest
julia> isa((1, 2, 3, 4, 5, 6), NTuple{6, Int})
true
```

Siehe auch [`ntuple`](@ref).
