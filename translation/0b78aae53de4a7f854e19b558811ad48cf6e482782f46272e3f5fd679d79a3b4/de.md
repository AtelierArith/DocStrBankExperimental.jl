```
Float32(x [, mode::RoundingMode])
```

Erstellt ein `Float32` aus `x`. Wenn `x` nicht genau darstellbar ist, bestimmt `mode`, wie `x` gerundet wird.

# Beispiele

```jldoctest
julia> Float32(1/3, RoundDown)
0.3333333f0

julia> Float32(1/3, RoundUp)
0.33333334f0
```

Siehe [`RoundingMode`](@ref) für verfügbare Rundungsmodi.
