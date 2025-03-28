```
mean(itr)
```

Berechne den Mittelwert aller Elemente in einer Sammlung.

!!! Hinweis     Wenn `itr` `NaN` oder [`missing`](@ref) Werte enthält, ist das Ergebnis ebenfalls `NaN` oder `missing` (`missing` hat Vorrang, wenn das Array beides enthält). Verwende die Funktion [`skipmissing`](@ref), um `missing`-Einträge zu ignorieren und den Mittelwert der nicht fehlenden Werte zu berechnen.

# Beispiele

```jldoctest
julia> using Statistics

julia> mean(1:20)
10.5

julia> mean([1, missing, 3])
missing

julia> mean(skipmissing([1, missing, 3]))
2.0
```
