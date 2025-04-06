```
div(x, y, r::RoundingMode=RoundToZero)
```

Le quotient de la division euclidienne (entière). Calcule `x / y`, arrondi à un entier selon le mode d'arrondi `r`. En d'autres termes, la quantité

```
round(x / y, r)
```

sans aucun arrondi intermédiaire.

!!! compat "Julia 1.4"
    La méthode à trois arguments prenant un `RoundingMode` nécessite Julia 1.4 ou une version ultérieure.


Voir aussi [`fld`](@ref) et [`cld`](@ref), qui sont des cas particuliers de cette fonction.

!!! compat "Julia 1.9"
    `RoundFromZero` nécessite au moins Julia 1.9.


# Exemples :

```jldoctest
julia> div(4, 3, RoundToZero) # Correspond à div(4, 3)
1
julia> div(4, 3, RoundDown) # Correspond à fld(4, 3)
1
julia> div(4, 3, RoundUp) # Correspond à cld(4, 3)
2
julia> div(5, 2, RoundNearest)
2
julia> div(5, 2, RoundNearestTiesAway)
3
julia> div(-5, 2, RoundNearest)
-2
julia> div(-5, 2, RoundNearestTiesAway)
-3
julia> div(-5, 2, RoundNearestTiesUp)
-2
julia> div(4, 3, RoundFromZero)
2
julia> div(-4, 3, RoundFromZero)
-2
```
