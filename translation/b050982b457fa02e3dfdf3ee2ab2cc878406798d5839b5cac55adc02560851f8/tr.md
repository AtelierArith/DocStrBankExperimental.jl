```
geev!(jobvl, jobvr, A) -> (W, VL, VR)
```

`A`'n özdeğer sistemini bulur. Eğer `jobvl = N` ise, `A`'nın sol özvektörleri hesaplanmaz. Eğer `jobvr = N` ise, `A`'nın sağ özvektörleri hesaplanmaz. Eğer `jobvl = V` veya `jobvr = V` ise, ilgili özvektörler hesaplanır. Özdeğerler `W`'de, sağ özvektörler `VR`'de ve sol özvektörler `VL`'de döner.
