```
findmin!(rval, rind, A) -> (minval, index)
```

Finde das Minimum von `A` und den entsprechenden linearen Index entlang der Singleton-Dimensionen von `rval` und `rind`, und speichere die Ergebnisse in `rval` und `rind`. `NaN` wird als kleiner als alle anderen Werte außer `missing` behandelt.

!!! warning
    Das Verhalten kann unerwartet sein, wenn ein mutiertes Argument Speicher mit einem anderen Argument teilt.

