```
ormrz!(side, trans, A, tau, C)
```

Matris `C`'yi `tzrzf!` ile sağlanan dönüşümden `Q` ile çarpar. `side` veya `trans`'a bağlı olarak çarpma sol taraflı (`side = L, Q*C`) veya sağ taraflı (`side = R, C*Q`) olabilir ve `Q` değiştirilmemiş (`trans = N`), transpoze edilmiş (`trans = T`) veya konjugat transpoze edilmiş (`trans = C`) olabilir. Çarpmanın sonucuyla yerinde değiştirilen matris `C`'yi döner.
