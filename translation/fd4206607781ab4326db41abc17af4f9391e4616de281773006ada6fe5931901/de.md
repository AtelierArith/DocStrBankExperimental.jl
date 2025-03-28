```
cov(X::AbstractMatrix; dims::Int=1, corrected::Bool=true)
```

Berechne die Kovarianzmatrix der Matrix `X` entlang der Dimension `dims`. Wenn `corrected` `true` ist (der Standardwert), wird die Summe mit `n-1` skaliert, während die Summe mit `n` skaliert wird, wenn `corrected` `false` ist, wobei `n = size(X, dims)` ist.
