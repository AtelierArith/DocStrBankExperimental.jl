```
cumsum!(B, A; dims::Integer)
```

`A`'nın `dims` boyutu boyunca kümülatif toplamını alır ve sonucu `B`'ye kaydeder. Ayrıca bkz. [`cumsum`](@ref).

!!! uyarı     Herhangi bir değiştirilmiş argümanın başka bir argümanla bellek paylaşması durumunda davranış beklenmedik olabilir.
