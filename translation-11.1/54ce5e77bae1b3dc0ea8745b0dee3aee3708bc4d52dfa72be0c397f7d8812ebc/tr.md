```
trevc!(side, howmny, select, T, VL = similar(T), VR = similar(T))
```

Üst üçgen matris `T`'nin özdeğer sistemini bulur. Eğer `side = R` ise, sağ özvektörler hesaplanır. Eğer `side = L` ise, sol özvektörler hesaplanır. Eğer `side = B` ise, her iki set de hesaplanır. Eğer `howmny = A` ise, tüm özvektörler bulunur. Eğer `howmny = B` ise, tüm özvektörler bulunur ve `VL` ve `VR` kullanılarak geri dönüştürülür. Eğer `howmny = S` ise, yalnızca `select` içindeki değerlere karşılık gelen özvektörler hesaplanır.
