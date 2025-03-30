```
ntuple(f, ::Val{N})
```

`N` uzunluğunda bir demet oluşturur, her bir elemanı `f(i)` olarak hesaplar; burada `i` elemanın indeksidir. `Val(N)` argümanını alarak, bu ntuple versiyonunun, uzunluğu bir tamsayı olarak alan versiyondan daha verimli kod üretebileceği mümkündür. Ancak `ntuple(f, N)`, `N` derleme zamanında belirlenemediğinde `ntuple(f, Val(N))`'den daha tercih edilir.

# Örnekler

```jldoctest
julia> ntuple(i -> 2*i, Val(4))
(2, 4, 6, 8)
```
