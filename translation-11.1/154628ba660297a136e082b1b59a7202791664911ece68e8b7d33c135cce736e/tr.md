```
getrs!(trans, A, ipiv, B)
```

Kare matris denklemini `A * X = B`, `transpose(A) * X = B` veya `adjoint(A) * X = B` çözer. Çözümü içindeki matris/vektör `B`'yi yerinde değiştirir. `A`, `getrf!`'den elde edilen `LU` faktorizasyonudur ve `ipiv` pivot bilgilerini içerir. `trans`, `N` (değişiklik yok), `T` (transpoze) veya `C` (konjugat transpoze) olabilir.
