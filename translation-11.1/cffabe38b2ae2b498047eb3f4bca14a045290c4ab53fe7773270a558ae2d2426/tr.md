```
hseqr!(job, compz, ilo, ihi, H, Z) -> (H, Z, w)
```

Bir matrisin Hessenberg formuna indirgenmiş tüm özdeğerlerini ve (isteğe bağlı olarak) Schur faktorizasyonunu hesaplar. Eğer `H` `gebal!` ile dengelenmişse, `ilo` ve `ihi` `gebal!`'nin çıktılarıdır. Aksi takdirde, `ilo = 1` ve `ihi = size(H,2)` olmalıdır. `tau`, faktorizasyonun temel yansıtıcılarını içerir.
