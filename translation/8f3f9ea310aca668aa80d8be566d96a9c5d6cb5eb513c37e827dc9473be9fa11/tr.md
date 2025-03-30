```
cov(x::AbstractVector, y::AbstractVector; corrected::Bool=true)
```

Vektörler `x` ve `y` arasındaki kovaryansı hesaplar. Eğer `corrected` `true` (varsayılan) ise, $\frac{1}{n-1}\sum_{i=1}^n (x_i-\bar x) (y_i-\bar y)^*$ hesaplanır; burada $*$ karmaşık konjugatı ve `n = length(x) = length(y)`'dir. Eğer `corrected` `false` ise, $\frac{1}{n}\sum_{i=1}^n (x_i-\bar x) (y_i-\bar y)^*$ hesaplanır.
