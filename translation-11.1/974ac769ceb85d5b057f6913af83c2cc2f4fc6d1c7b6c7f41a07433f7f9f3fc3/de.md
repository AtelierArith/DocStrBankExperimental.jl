```
median(itr)
```

Berechne den Median aller Elemente in einer Sammlung. Bei einer geraden Anzahl von Elementen existiert kein exakter Medianwert, sodass das Ergebnis dem Mittelwert von zwei Medianwerten entspricht.

!!! Hinweis     Wenn `itr` `NaN` oder [`missing`](@ref) Werte enthält, ist das Ergebnis ebenfalls `NaN` oder `missing` (`missing` hat Vorrang, wenn `itr` beide enthält). Verwende die Funktion [`skipmissing`](@ref), um `missing`-Einträge zu ignorieren und den Median der nicht fehlenden Werte zu berechnen.

# Beispiele

```jldoctest
julia> using Statistics

julia> median([1, 2, 3])
2.0

julia> median([1, 2, 3, 4])
2.5

julia> median([1, 2, missing, 4])
missing

julia> median(skipmissing([1, 2, missing, 4]))
2.0
```
