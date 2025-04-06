```
symdiff!(s::Union{AbstractSet,AbstractVector}, itrs...)
```

Konstruiere die symmetrische Differenz der übergebenen Mengen und überschreibe `s` mit dem Ergebnis. Wenn `s` ein Array ist, bleibt die Reihenfolge erhalten. Beachte, dass in diesem Fall die Häufigkeit der Elemente wichtig ist.

!!! warning
    Das Verhalten kann unerwartet sein, wenn ein veränderter Parameter Speicher mit einem anderen Parameter teilt.

