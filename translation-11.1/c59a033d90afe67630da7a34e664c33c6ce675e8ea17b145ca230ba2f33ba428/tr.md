```
schur(A, B) -> F::GenelleştirilmişSchur
```

Matrislerin `A` ve `B` Genel Schur (veya QZ) faktorizasyonunu hesaplar. (kuazi) üçgen Schur faktörleri `F` nesnesinden `F.S` ve `F.T` ile elde edilebilir, sol birim/ortogonal Schur vektörleri `F.left` veya `F.Q` ile elde edilebilir ve sağ birim/ortogonal Schur vektörleri `F.right` veya `F.Z` ile elde edilebilir, böylece `A=F.left*F.S*F.right'` ve `B=F.left*F.T*F.right'`. `A` ve `B`'nin genel özdeğerleri `F.α./F.β` ile elde edilebilir.

Ayrıştırmayı yinelemek, bileşenleri `F.S`, `F.T`, `F.Q`, `F.Z`, `F.α` ve `F.β` üretir.
