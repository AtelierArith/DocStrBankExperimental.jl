```
findmax!(rval, rind, A) -> (maxval, index)
```

`A`'nın maksimumunu ve `rval` ve `rind`'eki karşılık gelen lineer indeksleri bulur ve sonuçları `rval` ve `rind`'e kaydeder. `NaN`, `missing` hariç tüm diğer değerlerden daha büyük olarak kabul edilir.

!!! warning
    Herhangi bir değiştirilmiş argümanın, başka bir argümanla bellek paylaşması durumunda davranış beklenmedik olabilir.

