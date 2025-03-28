```
BigFloat(x::Union{Real, AbstractString} [, rounding::RoundingMode=rounding(BigFloat)]; [precision::Integer=precision(BigFloat)])
```

Créez un nombre à virgule flottante de précision arbitraire à partir de `x`, avec une précision `precision`. L'argument `rounding` spécifie la direction dans laquelle le résultat doit être arrondi si la conversion ne peut pas être effectuée exactement. S'il n'est pas fourni, ceux-ci sont définis par les valeurs globales actuelles.

`BigFloat(x::Real)` est identique à `convert(BigFloat,x)`, sauf si `x` est déjà un `BigFloat`, auquel cas il renverra une valeur avec la précision définie par la précision globale actuelle ; `convert` renverra toujours `x`.

`BigFloat(x::AbstractString)` est identique à [`parse`](@ref). Cela est fourni pour la commodité puisque les littéraux décimaux sont convertis en `Float64` lors de l'analyse, donc `BigFloat(2.1)` peut ne pas donner ce que vous attendez.

Voir aussi :

  * [`@big_str`](@ref)
  * [`rounding`](@ref) et [`setrounding`](@ref)
  * [`precision`](@ref) et [`setprecision`](@ref)

!!! compat "Julia 1.1"
    `precision` en tant qu'argument clé nécessite au moins Julia 1.1. Dans Julia 1.0, `precision` est le deuxième argument positionnel (`BigFloat(x, precision)`).


# Exemples

```jldoctest
julia> BigFloat(2.1) # 2.1 ici est un Float64
2.100000000000000088817841970012523233890533447265625

julia> BigFloat("2.1") # le BigFloat le plus proche de 2.1
2.099999999999999999999999999999999999999999999999999999999999999999999999999986

julia> BigFloat("2.1", RoundUp)
2.100000000000000000000000000000000000000000000000000000000000000000000000000021

julia> BigFloat("2.1", RoundUp, precision=128)
2.100000000000000000000000000000000000007
```
