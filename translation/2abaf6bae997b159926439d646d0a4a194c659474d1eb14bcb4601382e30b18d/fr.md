```
cis(x)
```

Méthode plus efficace pour `exp(im*x)` en utilisant la formule d'Euler : $\cos(x) + i \sin(x) = \exp(i x)$.

Voir aussi [`cispi`](@ref), [`sincos`](@ref), [`exp`](@ref), [`angle`](@ref).

# Exemples

```jldoctest
julia> cis(π) ≈ -1
true
```
