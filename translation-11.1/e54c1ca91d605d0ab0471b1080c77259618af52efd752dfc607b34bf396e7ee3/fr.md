```
rem2pi(x, r::RoundingMode)
```

Calcule le reste de `x` après la division entière par `2π`, avec le quotient arrondi selon le mode d'arrondi `r`. En d'autres termes, la quantité

```
x - 2π*round(x/(2π),r)
```

sans aucun arrondi intermédiaire. Cela utilise en interne une approximation de haute précision de 2π, et donnera donc un résultat plus précis que `rem(x,2π,r)`

  * si `r == RoundNearest`, alors le résultat est dans l'intervalle $[-π, π]$. Cela sera généralement le résultat le plus précis. Voir aussi [`RoundNearest`](@ref).
  * si `r == RoundToZero`, alors le résultat est dans l'intervalle $[0, 2π]$ si `x` est positif, ou $[-2π, 0]$ sinon. Voir aussi [`RoundToZero`](@ref).
  * si `r == RoundDown`, alors le résultat est dans l'intervalle $[0, 2π]$. Voir aussi [`RoundDown`](@ref).
  * si `r == RoundUp`, alors le résultat est dans l'intervalle $[-2π, 0]$. Voir aussi [`RoundUp`](@ref).

# Exemples

```jldoctest
julia> rem2pi(7pi/4, RoundNearest)
-0.7853981633974485

julia> rem2pi(7pi/4, RoundDown)
5.497787143782138
```
