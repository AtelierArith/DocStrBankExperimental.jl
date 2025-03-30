```
stein!(dv, ev_in, w_in, iblock_in, isplit_in)
```

Simetrik tridiagonal bir matris için özvektörleri hesaplar; `dv` diagonal ve `ev_in` ise dış-diyagonal olarak kullanılır. `w_in`, karşılık gelen özvektörleri bulmak için giriş özdeğerlerini belirtir. `iblock_in`, `w_in` içindeki özdeğerlere karşılık gelen alt matrisleri belirtir. `isplit_in`, alt matris blokları arasındaki bölme noktalarını belirtir.
