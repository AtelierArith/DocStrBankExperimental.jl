```
stegr!(jobz, range, dv, ev, vl, vu, il, iu) -> (w, Z)
```

Simetrik üçgen matris için özdeğerleri (`jobz = N`) veya özdeğerler ve özvektörler (`jobz = V`) hesaplar; `dv` diagonal ve `ev` off-diagonal olarak kullanılır. Eğer `range = A` ise, tüm özdeğerler bulunur. Eğer `range = V` ise, `(vl, vu]` yarı açık aralığında özdeğerler bulunur. Eğer `range = I` ise, `il` ve `iu` arasındaki indekslere sahip özdeğerler bulunur. Özdeğerler `w` içinde ve özvektörler `Z` içinde döndürülür.
