```
Inf, Inf64
```

L'infini positif de type [`Float64`](@ref).

Voir aussi : [`isfinite`](@ref), [`typemax`](@ref), [`NaN`](@ref), [`Inf32`](@ref).

# Exemples

```jldoctest
julia> π/0
Inf

julia> +1.0 / -0.0
-Inf

julia> ℯ^-Inf
0.0
```
