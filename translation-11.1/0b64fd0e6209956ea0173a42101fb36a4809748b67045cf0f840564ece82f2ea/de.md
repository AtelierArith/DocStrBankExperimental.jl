```
nextfloat(x::AbstractFloat)
```

Gibt die kleinste Fließkommazahl `y` des gleichen Typs wie `x` zurück, so dass `x < y`. Wenn kein solches `y` existiert (z. B. wenn `x` `Inf` oder `NaN` ist), wird `x` zurückgegeben.

Siehe auch: [`prevfloat`](@ref), [`eps`](@ref), [`issubnormal`](@ref).
