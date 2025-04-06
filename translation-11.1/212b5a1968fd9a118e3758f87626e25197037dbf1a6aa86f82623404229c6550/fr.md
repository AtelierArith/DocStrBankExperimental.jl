```
frexp(val)
```

Retourne `(x,exp)` tel que `x` a une magnitude dans l'intervalle $[1/2, 1)$ ou 0, et `val` est égal à $x \times 2^{exp}$.

Voir aussi [`significand`](@ref), [`exponent`](@ref), [`ldexp`](@ref).

# Exemples

```jldoctest
julia> frexp(6.0)
(0.75, 3)

julia> significand(6.0), exponent(6.0)  # intervalle [1, 2) à la place
(1.5, 2)

julia> frexp(0.0), frexp(NaN), frexp(-Inf)  # l'exposant donnerait une erreur
((0.0, 0), (NaN, 0), (-Inf, 0))
```
