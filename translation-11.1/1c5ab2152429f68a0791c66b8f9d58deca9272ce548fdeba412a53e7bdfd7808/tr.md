```
intersect!(s::Union{AbstractSet,AbstractVector}, itrs...)
```

Geçerli tüm küme kesişimlerini alır ve sonucu `s` ile değiştirir. Dizilerle sıralamayı korur.

!!! uyarı     Herhangi bir değiştirilmiş argümanın, diğer herhangi bir argümanla bellek paylaşması durumunda davranış beklenmedik olabilir.
