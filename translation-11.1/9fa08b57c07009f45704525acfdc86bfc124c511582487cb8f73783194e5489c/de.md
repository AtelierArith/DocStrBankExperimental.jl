```
findmax!(rval, rind, A) -> (maxval, index)
```

Finde das Maximum von `A` und den entsprechenden linearen Index entlang der Singleton-Dimensionen von `rval` und `rind`, und speichere die Ergebnisse in `rval` und `rind`. `NaN` wird als größer als alle anderen Werte außer `missing` behandelt.

!!! warning
    Das Verhalten kann unerwartet sein, wenn ein mutiertes Argument Speicher mit einem anderen Argument teilt.

