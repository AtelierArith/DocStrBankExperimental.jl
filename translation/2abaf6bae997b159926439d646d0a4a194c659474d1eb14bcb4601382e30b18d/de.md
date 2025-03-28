```
cis(x)
```

Effizientere Methode für `exp(im*x)` unter Verwendung der Eulerschen Formel: $\cos(x) + i \sin(x) = \exp(i x)$.

Siehe auch [`cispi`](@ref), [`sincos`](@ref), [`exp`](@ref), [`angle`](@ref).

# Beispiele

```jldoctest
julia> cis(π) ≈ -1
true
```
