```
cov(x::AbstractVector, y::AbstractVector; corrected::Bool=true)
```

Calcula la covarianza entre los vectores `x` y `y`. Si `corrected` es `true` (el valor predeterminado), calcula $\frac{1}{n-1}\sum_{i=1}^n (x_i-\bar x) (y_i-\bar y)^*$ donde $*$ denota el conjugado complejo y `n = length(x) = length(y)`. Si `corrected` es `false`, calcula $\frac{1}{n}\sum_{i=1}^n (x_i-\bar x) (y_i-\bar y)^*$.
