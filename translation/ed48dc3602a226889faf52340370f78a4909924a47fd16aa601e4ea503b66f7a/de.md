```
floorceil(dt::TimeType, p::Period) -> (TimeType, TimeType)
```

Gibt gleichzeitig den `floor` und `ceil` eines `Date` oder `DateTime` mit der Auflösung `p` zurück. Effizienter als die einzelnen Aufrufe von `floor` und `ceil`.
