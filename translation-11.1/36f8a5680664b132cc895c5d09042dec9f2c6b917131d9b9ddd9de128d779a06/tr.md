```
gbmv(trans, m, kl, ku, alpha, A, x)
```

[`trans`](@ref stdlib-blas-trans) göre `alpha*A*x` veya `alpha*A'*x` döndürün. Matris `A`, `kl` alt-diagonal ve `ku` üst-diagonal ile `m` boyutunda ve `size(A,2)` boyutunda genel bir bant matrisidir ve `alpha` bir skalar.
