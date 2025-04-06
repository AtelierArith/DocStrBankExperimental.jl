```
Float64(x [, mode::RoundingMode])
```

Erstellt ein `Float64` aus `x`. Wenn `x` nicht genau darstellbar ist, bestimmt `mode`, wie `x` gerundet wird.

# Beispiele

```jldoctest
julia> Float64(pi, RoundDown)
3.141592653589793

julia> Float64(pi, RoundUp)
3.1415926535897936
```

Siehe [`RoundingMode`](@ref) für verfügbare Rundungsmodi.
