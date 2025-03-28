```
Inf, Inf64
```

Positive Unendlichkeit vom Typ [`Float64`](@ref).

Siehe auch: [`isfinite`](@ref), [`typemax`](@ref), [`NaN`](@ref), [`Inf32`](@ref).

# Beispiele

```jldoctest
julia> π/0
Inf

julia> +1.0 / -0.0
-Inf

julia> ℯ^-Inf
0.0
```
