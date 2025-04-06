```
gbtrf!(kl, ku, m, AB) -> (AB, ipiv)
```

Bantlı bir matrisin `AB` LU faktorizasyonunu hesaplayın. `kl`, sıfır olmayan bir band içeren ilk alt diyagonal, `ku` ise birini içeren son üst diyagonaldir ve `m`, matris `AB`'nin ilk boyutudur. LU faktorizasyonunu yerinde döndürür ve kullanılan pivotların vektörü `ipiv`'i döndürür.
