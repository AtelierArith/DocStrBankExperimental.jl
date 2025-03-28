```
//(num, den)
```

Diviser deux entiers ou nombres rationnels, donnant un résultat de type [`Rational`](@ref). Plus généralement, `//` peut être utilisé pour la division rationnelle exacte d'autres types numériques avec des composants entiers ou rationnels, tels que des nombres complexes avec des composants entiers.

Notez que les arguments à virgule flottante ([`AbstractFloat`](@ref)) ne sont pas autorisés par `//` (même si les valeurs sont rationnelles). Les arguments doivent être des sous-types de [`Integer`](@ref), `Rational`, ou des composites de ceux-ci.

# Exemples

```jldoctest
julia> 3 // 5
3//5

julia> (3 // 5) // (2 // 1)
3//10

julia> (1+2im) // (3+4im)
11//25 + 2//25*im

julia> 1.0 // 2
ERROR: MethodError: no method matching //(::Float64, ::Int64)
[...]
```
