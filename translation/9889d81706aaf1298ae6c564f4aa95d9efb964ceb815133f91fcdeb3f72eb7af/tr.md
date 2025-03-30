```
circshift!(dest, src, shifts)
```

Dairesel kaydırma, yani döndürme, `src` içindeki verileri kaydırarak sonucu `dest` içinde saklar. `shifts`, her boyutta kaydırma miktarını belirtir.

!!! warning
    Herhangi bir değiştirilmiş argümanın, başka bir argümanla bellek paylaşması durumunda davranış beklenmedik olabilir.


Ayrıca bkz. [`circshift`](@ref).
