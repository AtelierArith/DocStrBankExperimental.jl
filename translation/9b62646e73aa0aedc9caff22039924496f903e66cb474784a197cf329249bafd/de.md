```
cov(x::AbstractVector; corrected::Bool=true)
```

Berechne die Varianz des Vektors `x`. Wenn `corrected` `true` ist (der Standardwert), wird die Summe mit `n-1` skaliert, während die Summe mit `n` skaliert wird, wenn `corrected` `false` ist, wobei `n = length(x)` ist.
