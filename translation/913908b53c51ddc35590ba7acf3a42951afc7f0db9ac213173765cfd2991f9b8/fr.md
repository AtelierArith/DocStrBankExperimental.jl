```
round([T,] x, [r::RoundingMode])
round(x, [r::RoundingMode]; digits::Integer=0, base = 10)
round(x, [r::RoundingMode]; sigdigits::Integer, base = 10)
```

Arrondit le nombre `x`.

Sans arguments de mot-clé, `x` est arrondi à une valeur entière, retournant une valeur de type `T`, ou du même type que `x` si aucun `T` n'est fourni. Une [`InexactError`](@ref) sera levée si la valeur n'est pas représentable par `T`, similaire à [`convert`](@ref).

Si l'argument de mot-clé `digits` est fourni, il arrondit au nombre spécifié de chiffres après la virgule décimale (ou avant si négatif), en base `base`.

Si l'argument de mot-clé `sigdigits` est fourni, il arrondit au nombre spécifié de chiffres significatifs, en base `base`.

Le [`RoundingMode`](@ref) `r` contrôle la direction de l'arrondi ; la valeur par défaut est [`RoundNearest`](@ref), qui arrondit à l'entier le plus proche, avec des égalités (valeurs fractionnaires de 0.5) arrondies à l'entier pair le plus proche. Notez que `round` peut donner des résultats incorrects si le mode d'arrondi global est changé (voir [`rounding`](@ref)).

Lors de l'arrondi à un type à virgule flottante, il arrondira aux entiers représentables par ce type (et Inf) plutôt qu'aux véritables entiers. Inf est traité comme un ulp supérieur à `floatmax(T)` aux fins de déterminer "le plus proche", similaire à [`convert`](@ref).

# Exemples

```jldoctest
julia> round(1.7)
2.0

julia> round(Int, 1.7)
2

julia> round(1.5)
2.0

julia> round(2.5)
2.0

julia> round(pi; digits=2)
3.14

julia> round(pi; digits=3, base=2)
3.125

julia> round(123.456; sigdigits=2)
120.0

julia> round(357.913; sigdigits=4, base=2)
352.0

julia> round(Float16, typemax(UInt128))
Inf16

julia> floor(Float16, typemax(UInt128))
Float16(6.55e4)
```

!!! note
    L'arrondi à des chiffres spécifiés dans des bases autres que 2 peut être inexact lors de l'opération sur des nombres à virgule flottante binaire. Par exemple, la valeur [`Float64`](@ref) représentée par `1.15` est en réalité *inférieure* à 1.15, mais sera arrondie à 1.2. Par exemple :

    ```jldoctest
    julia> x = 1.15
    1.15

    julia> big(1.15)
    1.149999999999999911182158029987476766109466552734375

    julia> x < 115//100
    true

    julia> round(x, digits=1)
    1.2
    ```


# Extensions

Pour étendre `round` à de nouveaux types numériques, il est généralement suffisant de définir `Base.round(x::NewType, r::RoundingMode)`. ```
