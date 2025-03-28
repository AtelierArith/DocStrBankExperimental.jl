```
Inf, Inf64
```

Infinito positivo de tipo [`Float64`](@ref).

Véase también: [`isfinite`](@ref), [`typemax`](@ref), [`NaN`](@ref), [`Inf32`](@ref).

# Ejemplos

```jldoctest
julia> π/0
Inf

julia> +1.0 / -0.0
-Inf

julia> ℯ^-Inf
0.0
```
