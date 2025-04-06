```
ndigits(n::Integer; base::Integer=10, pad::Integer=1)
```

Berechne die Anzahl der Ziffern in der Ganzzahl `n`, die in der Basis `base` geschrieben ist (`base` darf nicht in `[-1, 0, 1]` sein), optional mit Nullen auf eine bestimmte Größe aufgepolstert (das Ergebnis wird niemals kleiner als `pad` sein).

Siehe auch [`digits`](@ref), [`count_ones`](@ref).

# Beispiele

```jldoctest
julia> ndigits(0)
1

julia> ndigits(12345)
5

julia> ndigits(1022, base=16)
3

julia> string(1022, base=16)
"3fe"

julia> ndigits(123, pad=5)
5

julia> ndigits(-123)
3
```
