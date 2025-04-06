```
exp(x)
```

Berechne die natürliche Basisexponentialfunktion von `x`, mit anderen Worten $ℯ^x$.

Siehe auch [`exp2`](@ref), [`exp10`](@ref) und [`cis`](@ref).

# Beispiele

```jldoctest
julia> exp(1.0)
2.718281828459045

julia> exp(im * pi) ≈ cis(pi)
true
```
