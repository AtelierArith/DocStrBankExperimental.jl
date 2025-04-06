```
cov(X::AbstractVecOrMat, Y::AbstractVecOrMat; dims::Int=1, corrected::Bool=true)
```

Berechnet die Kovarianz zwischen den Vektoren oder Matrizen `X` und `Y` entlang der Dimension `dims`. Wenn `corrected` `true` ist (der Standardwert), wird die Summe mit `n-1` skaliert, während die Summe mit `n` skaliert wird, wenn `corrected` `false` ist, wobei `n = size(X, dims) = size(Y, dims)`.
