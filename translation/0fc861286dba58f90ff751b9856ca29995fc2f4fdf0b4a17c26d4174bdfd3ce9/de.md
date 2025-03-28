```
floorceil(x::Period, precision::T) where T <: Union{TimePeriod, Week, Day} -> (T, T)
```

Gibt gleichzeitig den `floor` und `ceil` von `Period` mit der Auflösung `p` zurück. Effizienter als die einzelnen Aufrufe von `floor` und `ceil`.
