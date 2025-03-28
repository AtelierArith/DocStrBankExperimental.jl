```
fld(x, y)
```

Plus grand entier inférieur ou égal à `x / y`. Équivalent à `div(x, y, RoundDown)`.

Voir aussi [`div`](@ref), [`cld`](@ref), [`fld1`](@ref).

# Exemples

```jldoctest
julia> fld(7.3, 5.5)
1.0

julia> fld.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) avec eltype Int64:
 -2  -2  -1  -1  -1  0  0  0  1  1  1
```

Parce que `fld(x, y)` implémente un arrondi à l'entier inférieur strictement correct basé sur la valeur réelle des nombres à virgule flottante, des situations non intuitives peuvent survenir. Par exemple :

```jldoctest
julia> fld(6.0, 0.1)
59.0
julia> 6.0 / 0.1
60.0
julia> 6.0 / big(0.1)
59.99999999999999666933092612453056361837965690217069245739573412231113406246995
```

Ce qui se passe ici, c'est que la valeur réelle du nombre à virgule flottante écrit comme `0.1` est légèrement supérieure à la valeur numérique 1/10 tandis que `6.0` représente le nombre 6 avec précision. Par conséquent, la valeur réelle de `6.0 / 0.1` est légèrement inférieure à 60. Lors de la division, cela est arrondi à précisément `60.0`, mais `fld(6.0, 0.1)` prend toujours le plancher de la valeur réelle, donc le résultat est `59.0`.
