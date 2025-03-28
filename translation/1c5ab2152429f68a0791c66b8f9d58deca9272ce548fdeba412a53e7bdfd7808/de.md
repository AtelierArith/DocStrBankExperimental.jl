```
intersect!(s::Union{AbstractSet,AbstractVector}, itrs...)
```

Kreuzt alle übergebenen Mengen und überschreibt `s` mit dem Ergebnis. Behalte die Reihenfolge bei Arrays bei.

!!! warning
    Das Verhalten kann unerwartet sein, wenn ein mutiertes Argument Speicher mit einem anderen Argument teilt.

