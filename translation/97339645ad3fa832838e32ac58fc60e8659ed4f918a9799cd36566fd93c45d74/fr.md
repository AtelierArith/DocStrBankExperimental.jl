```
cis(A::AbstractMatrix)
```

Méthode plus efficace pour `exp(im*A)` de la matrice carrée `A` (surtout si `A` est `Hermitienne` ou `Symétrique` réel).

Voir aussi [`cispi`](@ref), [`sincos`](@ref), [`exp`](@ref).

!!! compat "Julia 1.7"
    Le support de l'utilisation de `cis` avec des matrices a été ajouté dans Julia 1.7.


# Exemples

```jldoctest
julia> cis([π 0; 0 π]) ≈ -I
true
```
