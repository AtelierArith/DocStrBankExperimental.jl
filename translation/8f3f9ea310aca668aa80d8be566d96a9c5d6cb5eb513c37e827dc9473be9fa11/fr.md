```
cov(x::AbstractVector, y::AbstractVector; corrected::Bool=true)
```

Calcule la covariance entre les vecteurs `x` et `y`. Si `corrected` est `true` (par défaut), calcule $\frac{1}{n-1}\sum_{i=1}^n (x_i-\bar x) (y_i-\bar y)^*$ où $*$ désigne le conjugué complexe et `n = length(x) = length(y)`. Si `corrected` est `false`, calcule $\frac{1}{n}\sum_{i=1}^n (x_i-\bar x) (y_i-\bar y)^*$.
