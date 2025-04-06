```
cov(x::AbstractVector; corrected::Bool=true)
```

Calcule la variance du vecteur `x`. Si `corrected` est `true` (par défaut), alors la somme est mise à l'échelle avec `n-1`, tandis que la somme est mise à l'échelle avec `n` si `corrected` est `false`, où `n = length(x)`.
