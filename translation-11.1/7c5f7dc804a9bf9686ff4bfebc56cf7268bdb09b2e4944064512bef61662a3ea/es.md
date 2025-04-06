```
cispi(x)
```

Método más preciso para `cis(pi*x)` (especialmente para grandes `x`).

Véase también [`cis`](@ref), [`sincospi`](@ref), [`exp`](@ref), [`angle`](@ref).

# Ejemplos

```jldoctest
julia> cispi(10000)
1.0 + 0.0im

julia> cispi(0.25 + 1im)
0.030556854645954562 + 0.03055685464595456im
```

!!! compat "Julia 1.6"
    Esta función requiere Julia 1.6 o posterior.

