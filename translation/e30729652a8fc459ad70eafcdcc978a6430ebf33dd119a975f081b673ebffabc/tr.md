```
gbtrs!(trans, kl, ku, m, AB, ipiv, B)
```

`AB * X = B` denklemini çözer. `trans`, `AB`'nin yönünü belirler. `N` (transpoze yok), `T` (transpoze) veya `C` (konjugat transpoze) olabilir. `kl`, sıfır olmayan bir band içeren ilk alt diyagonal, `ku` ise birini içeren son üst diyagonal ve `m`, `AB` matrisinin ilk boyutudur. `ipiv`, `gbtrf!`'den dönen pivotlar vektörüdür. `B`'yi yerinde değiştirerek `X` vektörünü veya matrisini döner.
