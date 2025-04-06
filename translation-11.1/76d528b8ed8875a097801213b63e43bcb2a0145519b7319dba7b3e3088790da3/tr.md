```
stebz!(range, order, vl, vu, il, iu, abstol, dv, ev) -> (dv, iblock, isplit)
```

Simetrik tridiagonal bir matris için özdeğerleri hesaplar; `dv` diagonal ve `ev` off-diagonal olarak kullanılır. Eğer `range = A` ise, tüm özdeğerler bulunur. Eğer `range = V` ise, `(vl, vu]` yarı açık aralığında özdeğerler bulunur. Eğer `range = I` ise, `il` ve `iu` arasındaki indekslere sahip özdeğerler bulunur. Eğer `order = B` ise, özdeğerler bir blok içinde sıralanır. Eğer `order = E` ise, tüm bloklar arasında sıralanır. `abstol`, yakınsama için bir tolerans olarak ayarlanabilir.
