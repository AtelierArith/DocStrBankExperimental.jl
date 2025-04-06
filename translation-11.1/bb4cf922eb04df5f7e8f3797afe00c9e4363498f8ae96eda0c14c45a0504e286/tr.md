```
Inf, Inf64
```

[`Float64`](@ref) türünde pozitif sonsuz.

Ayrıca bakınız: [`isfinite`](@ref), [`typemax`](@ref), [`NaN`](@ref), [`Inf32`](@ref).

# Örnekler

```jldoctest
julia> π/0
Inf

julia> +1.0 / -0.0
-Inf

julia> ℯ^-Inf
0.0
```
