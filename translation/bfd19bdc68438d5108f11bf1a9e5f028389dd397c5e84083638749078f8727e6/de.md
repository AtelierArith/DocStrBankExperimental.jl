```
widemul(x, y)
```

Multipliziere `x` und `y` und gebe das Ergebnis als einen größeren Typ zurück.

Siehe auch [`promote`](@ref), [`Base.add_sum`](@ref).

# Beispiele

```jldoctest
julia> widemul(Float32(3.0), 4.0) isa BigFloat
true

julia> typemax(Int8) * typemax(Int8)
1

julia> widemul(typemax(Int8), typemax(Int8))  # == 127^2
16129
```
