```
cispi(x)
```

Genaueres Verfahren für `cis(pi*x)` (insbesondere für große `x`).

Siehe auch [`cis`](@ref), [`sincospi`](@ref), [`exp`](@ref), [`angle`](@ref).

# Beispiele

```jldoctest
julia> cispi(10000)
1.0 + 0.0im

julia> cispi(0.25 + 1im)
0.030556854645954562 + 0.03055685464595456im
```

!!! compat "Julia 1.6"
    Diese Funktion erfordert Julia 1.6 oder höher.

