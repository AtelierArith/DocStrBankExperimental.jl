```
ggev3!(jobvl, jobvr, A, B) -> (alpha, beta, vl, vr)
```

`A` ve `B`'nin genel özdeğişken ayrıştırmasını bloklu bir algoritma kullanarak bulur. Eğer `jobvl = N` ise, sol özvektörler hesaplanmaz. Eğer `jobvr = N` ise, sağ özvektörler hesaplanmaz. Eğer `jobvl = V` veya `jobvr = V` ise, ilgili özvektörler hesaplanır. Bu fonksiyon LAPACK 3.6.0 gerektirir.
