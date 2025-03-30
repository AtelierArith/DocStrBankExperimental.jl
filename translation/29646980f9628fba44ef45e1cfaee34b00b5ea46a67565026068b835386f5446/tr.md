```
gehrd!(ilo, ihi, A) -> (A, tau)
```

Bir matris `A`'yı Hessenberg formuna dönüştürür. Eğer `A`, `gebal!` ile dengelenmişse, `ilo` ve `ihi` `gebal!`'nin çıktılarıdır. Aksi takdirde, `ilo = 1` ve `ihi = size(A,2)` olmalıdır. `tau`, faktorizasyonun temel yansıtıcılarını içerir.
