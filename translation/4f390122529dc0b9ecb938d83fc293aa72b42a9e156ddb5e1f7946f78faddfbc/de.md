```
div(x, y, r::RoundingMode=RoundToZero)
```

Der Quotient aus der euklidischen (ganzzahligen) Division. Berechnet `x / y`, gerundet auf eine ganze Zahl gemäß dem Rundungsmodus `r`. Mit anderen Worten, die Größe

```
round(x / y, r)
```

ohne Zwischenrundung.

!!! compat "Julia 1.4"
    Die Methode mit drei Argumenten, die einen `RoundingMode` verwendet, erfordert Julia 1.4 oder höher.


Siehe auch [`fld`](@ref) und [`cld`](@ref), die spezielle Fälle dieser Funktion sind.

!!! compat "Julia 1.9"
    `RoundFromZero` erfordert mindestens Julia 1.9.


# Beispiele:

```jldoctest
julia> div(4, 3, RoundToZero) # Entspricht div(4, 3)
1
julia> div(4, 3, RoundDown) # Entspricht fld(4, 3)
1
julia> div(4, 3, RoundUp) # Entspricht cld(4, 3)
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
