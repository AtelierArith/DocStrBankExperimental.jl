```
ldiv!(A::Tridiagonal, B::AbstractVecOrMat) -> B
```

`A \ B` をガウス消去法を用いて部分ピボットを行い、結果を `B` に格納して返します。この過程で、`A` の対角成分も上書きされます。

!!! compat "Julia 1.11"
    `Tridiagonal` 左辺に対する `ldiv!` は少なくとも Julia 1.11 が必要です。

