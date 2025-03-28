```
cov(X::AbstractMatrix; dims::Int=1, corrected::Bool=true)
```

Calcule la matrice de covariance de la matrice `X` le long de la dimension `dims`. Si `corrected` est `true` (par défaut), alors la somme est mise à l'échelle avec `n-1`, tandis que la somme est mise à l'échelle avec `n` si `corrected` est `false`, où `n = size(X, dims)`.
