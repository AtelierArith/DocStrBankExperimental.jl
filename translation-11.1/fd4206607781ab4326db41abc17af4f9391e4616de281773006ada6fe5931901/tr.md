```
cov(X::AbstractMatrix; dims::Int=1, corrected::Bool=true)
```

Matris `X`'in `dims` boyutu boyunca kovaryans matrisini hesaplar. Eğer `corrected` `true` (varsayılan) ise, toplam `n-1` ile ölçeklendirilir; `corrected` `false` ise toplam `n` ile ölçeklendirilir, burada `n = size(X, dims)`.
