```
symdiff!(s::Union{AbstractSet,AbstractVector}, itrs...)
```

Geçilen kümelerin simetrik farkını oluşturur ve `s`'yi sonuçla günceller. `s` bir dizi olduğunda, sıralama korunur. Bu durumda, elemanların çokluluğu önemlidir.

!!! uyarı     Herhangi bir değiştirilmiş argümanın başka bir argümanla bellek paylaşması durumunda davranış beklenmedik olabilir.
