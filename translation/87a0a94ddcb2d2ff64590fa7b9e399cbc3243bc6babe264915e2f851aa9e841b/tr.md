```
gttrf!(dl, d, du) -> (dl, d, du, du2, ipiv)
```

`dl` alt altındaki, `d` ana diyagonal üzerindeki ve `du` üst diyagonal üzerindeki bir üçgen matrisin `LU` faktorizasyonunu bulur.

`dl`, `d` ve `du` yerinde değiştirilir ve bunları, ikinci üst diyagonal `du2` ve pivot vektörü `ipiv` ile birlikte döner.
