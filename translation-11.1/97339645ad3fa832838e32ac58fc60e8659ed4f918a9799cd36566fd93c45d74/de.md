```
cis(A::AbstractMatrix)
```

Effizientere Methode für `exp(im*A)` einer quadratischen Matrix `A` (insbesondere wenn `A` `Hermitesch` oder reell-`symmetrisch` ist).

Siehe auch [`cispi`](@ref), [`sincos`](@ref), [`exp`](@ref).

!!! compat "Julia 1.7"
    Unterstützung für die Verwendung von `cis` mit Matrizen wurde in Julia 1.7 hinzugefügt.


# Beispiele

```jldoctest
julia> cis([π 0; 0 π]) ≈ -I
true
```
