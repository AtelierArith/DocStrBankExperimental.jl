```
cov(x::AbstractVector; corrected::Bool=true)
```

Calcula la varianza del vector `x`. Si `corrected` es `true` (el valor por defecto), entonces la suma se escala con `n-1`, mientras que la suma se escala con `n` si `corrected` es `false`, donde `n = length(x)`.
