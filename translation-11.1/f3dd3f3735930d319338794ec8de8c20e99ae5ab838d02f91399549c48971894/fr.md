```
significand(x)
```

Extraire le significand (a.k.a. mantisse) d'un nombre à virgule flottante. Si `x` est un nombre fini non nul, alors le résultat sera un nombre du même type et signe que `x`, et dont la valeur absolue est dans l'intervalle $[1,2)$. Sinon, `x` est retourné.

Voir aussi [`frexp`](@ref), [`exponent`](@ref).

# Exemples

```jldoctest
julia> significand(15.2)
1.9

julia> significand(-15.2)
-1.9

julia> significand(-15.2) * 2^3
-15.2

julia> significand(-Inf), significand(Inf), significand(NaN)
(-Inf, Inf, NaN)
```
