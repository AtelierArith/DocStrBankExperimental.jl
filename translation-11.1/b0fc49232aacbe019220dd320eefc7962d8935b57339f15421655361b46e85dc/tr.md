```
ggev!(jobvl, jobvr, A, B) -> (alpha, beta, vl, vr)
```

`A` ve `B`'nin genelleştirilmiş özdeğişken ayrıştırmasını bulur. Eğer `jobvl = N` ise, sol özvektörler hesaplanmaz. Eğer `jobvr = N` ise, sağ özvektörler hesaplanmaz. Eğer `jobvl = V` veya `jobvr = V` ise, ilgili özvektörler hesaplanır.
