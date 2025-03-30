```
cov(X::AbstractVecOrMat, Y::AbstractVecOrMat; dims::Int=1, corrected::Bool=true)
```

`X` ve `Y` vektörleri veya matrisleri arasında `dims` boyutu boyunca kovaryansı hesaplar. Eğer `corrected` `true` (varsayılan) ise, toplam `n-1` ile ölçeklendirilir, `corrected` `false` ise toplam `n` ile ölçeklendirilir; burada `n = size(X, dims) = size(Y, dims)`.
