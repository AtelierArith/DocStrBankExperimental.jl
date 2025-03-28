```
clamp(x, T)::T
```

Begrenze `x` zwischen `typemin(T)` und `typemax(T)` und konvertiere das Ergebnis in den Typ `T`.

Siehe auch [`trunc`](@ref).

# Beispiele

```jldoctest
julia> clamp(200, Int8)
127

julia> clamp(-200, Int8)
-128

julia> trunc(Int, 4pi^2)
39
```
