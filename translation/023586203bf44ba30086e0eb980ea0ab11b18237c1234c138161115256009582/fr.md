```
cov(X::AbstractVecOrMat, Y::AbstractVecOrMat; dims::Int=1, corrected::Bool=true)
```

Calcule la covariance entre les vecteurs ou matrices `X` et `Y` le long de la dimension `dims`. Si `corrected` est `true` (par défaut), alors la somme est mise à l'échelle avec `n-1`, tandis que la somme est mise à l'échelle avec `n` si `corrected` est `false`, où `n = size(X, dims) = size(Y, dims)`.
