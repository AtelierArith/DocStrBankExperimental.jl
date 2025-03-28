```
rem(x, y, r::RoundingMode=RoundToZero)
```

Calcule le reste de `x` après la division entière par `y`, avec le quotient arrondi selon le mode d'arrondi `r`. En d'autres termes, la quantité

```
x - y * round(x / y, r)
```

sans aucun arrondi intermédiaire.

  * si `r == RoundNearest`, alors le résultat est exact, et dans l'intervalle $[-|y| / 2, |y| / 2]$. Voir aussi [`RoundNearest`](@ref).
  * si `r == RoundToZero` (par défaut), alors le résultat est exact, et dans l'intervalle $[0, |y|)$ si `x` est positif, ou $(-|y|, 0]$ sinon. Voir aussi [`RoundToZero`](@ref).
  * si `r == RoundDown`, alors le résultat est dans l'intervalle $[0, y)$ si `y` est positif, ou $(y, 0]$ sinon. Le résultat peut ne pas être exact si `x` et `y` ont des signes différents, et `abs(x) < abs(y)`. Voir aussi [`RoundDown`](@ref).
  * si `r == RoundUp`, alors le résultat est dans l'intervalle $(-y, 0]$ si `y` est positif, ou $[0, -y)$ sinon. Le résultat peut ne pas être exact si `x` et `y` ont le même signe, et `abs(x) < abs(y)`. Voir aussi [`RoundUp`](@ref).
  * si `r == RoundFromZero`, alors le résultat est dans l'intervalle $(-y, 0]$ si `y` est positif, ou $[0, -y)$ sinon. Le résultat peut ne pas être exact si `x` et `y` ont le même signe, et `abs(x) < abs(y)`. Voir aussi [`RoundFromZero`](@ref).

!!! compat "Julia 1.9"
    `RoundFromZero` nécessite au moins Julia 1.9.


# Exemples :

```jldoctest
julia> x = 9; y = 4;

julia> x % y  # même que rem(x, y)
1

julia> x ÷ y  # même que div(x, y)
2

julia> x == div(x, y) * y + rem(x, y)
true
```
