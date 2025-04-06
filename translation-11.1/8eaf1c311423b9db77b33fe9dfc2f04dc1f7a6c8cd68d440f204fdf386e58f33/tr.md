```
ldiv!(A::Tridiagonal, B::AbstractVecOrMat) -> B
```

`A \ B` işlemini, kısmi pivotlama ile Gauss eliminasyonu kullanarak yerinde hesaplayın ve sonucu `B`'ye kaydedin, sonucu döndürün. Bu süreçte, `A`'nın diyagonal elemanları da üzerine yazılır.

!!! uyumluluk "Julia 1.11"
    `Tridiagonal` sol tarafları için `ldiv!`, en az Julia 1.11 gerektirir.

