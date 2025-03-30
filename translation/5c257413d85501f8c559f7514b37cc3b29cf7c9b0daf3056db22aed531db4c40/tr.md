```
cumprod!(B, A; dims::Integer)
```

`A`'nın `dims` boyutu boyunca kümülatif çarpımını alır ve sonucu `B`'ye kaydeder. Ayrıca [`cumprod`](@ref) bakınız.

!!! uyarı     Herhangi bir değiştirilmiş argümanın başka bir argümanla bellek paylaşması durumunda davranış beklenmedik olabilir.
