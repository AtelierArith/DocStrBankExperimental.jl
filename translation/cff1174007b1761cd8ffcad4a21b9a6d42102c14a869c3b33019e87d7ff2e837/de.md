```
round(z::Complex[, RoundingModeReal, [RoundingModeImaginary]])
round(z::Complex[, RoundingModeReal, [RoundingModeImaginary]]; digits=0, base=10)
round(z::Complex[, RoundingModeReal, [RoundingModeImaginary]]; sigdigits, base=10)
```

Gibt den nächstgelegenen ganzzahligen Wert des gleichen Typs wie der komplexe Wert `z` zurück, wobei bei Gleichständen die angegebenen [`RoundingMode`](@ref)s verwendet werden. Der erste [`RoundingMode`](@ref) wird zum Runden der reellen Komponenten verwendet, während der zweite zum Runden der imaginären Komponenten verwendet wird.

`RoundingModeReal` und `RoundingModeImaginary` standardmäßig auf [`RoundNearest`](@ref), das auf die nächste ganze Zahl rundet, wobei Gleichstände (Bruchwerte von 0,5) auf die nächste gerade ganze Zahl gerundet werden.

# Beispiele

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
