```
findmin!(rval, rind, A) -> (minval, index)
```

`A`'n minimum'unu ve `rval` ve `rind`'in tekil boyutları boyunca karşılık gelen lineer indeksini bulur ve sonuçları `rval` ve `rind`'e kaydeder. `NaN`, `missing` hariç tüm diğer değerlerden daha küçük olarak kabul edilir.

!!! uyarı     Herhangi bir değiştirilmiş argümanın, başka bir argümanla bellek paylaşması durumunda davranış beklenmedik olabilir.
