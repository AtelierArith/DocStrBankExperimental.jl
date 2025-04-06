```
prevfloat(x::AbstractFloat)
```

Gibt die größte Fließkommazahl `y` vom gleichen Typ wie `x` zurück, so dass `y < x`. Wenn kein solches `y` existiert (z. B. wenn `x` `-Inf` oder `NaN` ist), dann wird `x` zurückgegeben.
