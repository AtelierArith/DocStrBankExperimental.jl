```
cov(X::AbstractVecOrMat, Y::AbstractVecOrMat; dims::Int=1, corrected::Bool=true)
```

Calcula la covarianza entre los vectores o matrices `X` y `Y` a lo largo de la dimensión `dims`. Si `corrected` es `true` (el valor predeterminado), entonces la suma se escala con `n-1`, mientras que la suma se escala con `n` si `corrected` es `false`, donde `n = size(X, dims) = size(Y, dims)`.
