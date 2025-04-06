```
cov(x::AbstractVector, y::AbstractVector; corrected::Bool=true)
```

Berechnet die Kovarianz zwischen den Vektoren `x` und `y`. Wenn `corrected` `true` ist (der Standardwert), berechnet es $\frac{1}{n-1}\sum_{i=1}^n (x_i-\bar x) (y_i-\bar y)^*$, wobei $*$ den komplexen Konjugierten bezeichnet und `n = length(x) = length(y)`. Wenn `corrected` `false` ist, berechnet es $\frac{1}{n}\sum_{i=1}^n (x_i-\bar x) (y_i-\bar y)^*$.
