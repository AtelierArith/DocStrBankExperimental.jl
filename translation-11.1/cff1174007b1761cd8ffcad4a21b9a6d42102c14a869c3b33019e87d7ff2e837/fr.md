```
round(z::Complex[, RoundingModeReal, [RoundingModeImaginary]])
round(z::Complex[, RoundingModeReal, [RoundingModeImaginary]]; digits=0, base=10)
round(z::Complex[, RoundingModeReal, [RoundingModeImaginary]]; sigdigits, base=10)
```

Retourne la valeur intégrale la plus proche du même type que le `z` à valeurs complexes, en cas d'égalité, en utilisant les [`RoundingMode`](@ref) spécifiés. Le premier [`RoundingMode`](@ref) est utilisé pour arrondir les composants réels tandis que le second est utilisé pour arrondir les composants imaginaires.

`RoundingModeReal` et `RoundingModeImaginary` par défaut à [`RoundNearest`](@ref), qui arrondit à l'entier le plus proche, avec des égalités (valeurs fractionnelles de 0.5) arrondies à l'entier pair le plus proche.

# Exemples

```jldoctest
julia> round(3.14 + 4.5im)
3.0 + 4.0im

julia> round(3.14 + 4.5im, RoundUp, RoundNearestTiesUp)
4.0 + 5.0im

julia> round(3.14159 + 4.512im; digits = 1)
3.1 + 4.5im

julia> round(3.14159 + 4.512im; sigdigits = 3)
3.14 + 4.51im
```
