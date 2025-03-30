```
cov(x::AbstractVector; corrected::Bool=true)
```

Vektör `x`'in varyansını hesaplar. Eğer `corrected` `true` (varsayılan) ise, toplam `n-1` ile ölçeklendirilir; `corrected` `false` ise toplam `n` ile ölçeklendirilir, burada `n = length(x)`.
