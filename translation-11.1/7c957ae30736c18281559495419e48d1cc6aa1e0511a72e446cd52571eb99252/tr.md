```
stev!(job, dv, ev) -> (dv, Zmat)
```

Simetrik üçgen matris için özdeğer sistemini hesaplar; `dv` diagonal ve `ev` ise off-diagonal olarak kullanılır. Eğer `job = N` ise yalnızca özdeğerler bulunur ve `dv` içinde döndürülür. Eğer `job = V` ise özvektörler de bulunur ve `Zmat` içinde döndürülür.
