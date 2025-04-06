```
round([T,] x, [r::RoundingMode])
round(x, [r::RoundingMode]; digits::Integer=0, base = 10)
round(x, [r::RoundingMode]; sigdigits::Integer, base = 10)
```

Rundet die Zahl `x`.

Ohne Schlüsselwortargumente wird `x` auf einen ganzzahligen Wert gerundet, wobei ein Wert vom Typ `T` zurückgegeben wird, oder vom gleichen Typ wie `x`, wenn kein `T` angegeben ist. Ein [`InexactError`](@ref) wird ausgelöst, wenn der Wert nicht durch `T` darstellbar ist, ähnlich wie bei [`convert`](@ref).

Wenn das Schlüsselwortargument `digits` angegeben ist, wird auf die angegebene Anzahl von Ziffern nach dem Dezimalpunkt (oder davor, wenn negativ) in der Basis `base` gerundet.

Wenn das Schlüsselwortargument `sigdigits` angegeben ist, wird auf die angegebene Anzahl von signifikanten Ziffern in der Basis `base` gerundet.

Der [`RoundingMode`](@ref) `r` steuert die Richtung des Rundens; der Standard ist [`RoundNearest`](@ref), das auf die nächste ganze Zahl rundet, wobei bei Gleichständen (Bruchwerte von 0.5) auf die nächste gerade ganze Zahl gerundet wird. Beachten Sie, dass `round` falsche Ergebnisse liefern kann, wenn der globale Rundungsmodus geändert wird (siehe [`rounding`](@ref)).

Beim Runden auf einen Fließkommatyp wird auf ganze Zahlen gerundet, die von diesem Typ (und Inf) darstellbar sind, anstatt auf echte ganze Zahlen. Inf wird als eine ulp größer als das `floatmax(T)` behandelt, um "nächste" zu bestimmen, ähnlich wie bei [`convert`](@ref).

# Beispiele

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

!!! Hinweis     Das Runden auf angegebene Ziffern in Basen, die nicht 2 sind, kann ungenau sein, wenn mit binären Fließkommazahlen gearbeitet wird. Zum Beispiel ist der [`Float64`](@ref) Wert, der durch `1.15` dargestellt wird, tatsächlich *weniger* als 1.15, wird jedoch auf 1.2 gerundet. Zum Beispiel:

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


# Erweiterungen

Um `round` auf neue numerische Typen zu erweitern, ist es typischerweise ausreichend, `Base.round(x::NewType, r::RoundingMode)` zu definieren.
```
