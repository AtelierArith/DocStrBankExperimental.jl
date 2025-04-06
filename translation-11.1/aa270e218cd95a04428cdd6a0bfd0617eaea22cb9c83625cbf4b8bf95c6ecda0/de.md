```
stdm(itr, mean; corrected::Bool=true[, dims])
```

Berechne die Stichprobenstandardabweichung der Sammlung `itr`, mit bekannten Mittelwert(en) `mean`.

Der Algorithmus gibt einen Schätzer der Standardabweichung der generativen Verteilung zurück, unter der Annahme, dass jeder Eintrag von `itr` eine Stichprobe aus derselben unbekannten Verteilung ist, wobei die Stichproben unkorreliert sind. Für Arrays entspricht diese Berechnung der Berechnung von `sqrt(sum((itr .- mean(itr)).^2) / (length(itr) - 1))`. Wenn `corrected` `true` ist, wird die Summe mit `n-1` skaliert, während die Summe mit `n` skaliert wird, wenn `corrected` `false` ist, wobei `n` die Anzahl der Elemente in `itr` ist.

Wenn `itr` ein `AbstractArray` ist, können `dims` angegeben werden, um die Standardabweichung über Dimensionen zu berechnen. In diesem Fall muss `mean` ein Array mit derselben Form wie `mean(itr, dims=dims)` sein (zusätzliche nachfolgende Singleton-Dimensionen sind erlaubt).

!!! note
    Wenn das Array `NaN` oder [`missing`](@ref) Werte enthält, ist das Ergebnis ebenfalls `NaN` oder `missing` (`missing` hat Vorrang, wenn das Array beide enthält). Verwenden Sie die Funktion [`skipmissing`](@ref), um `missing`-Einträge zu überspringen und die Standardabweichung der nicht fehlenden Werte zu berechnen.


```
