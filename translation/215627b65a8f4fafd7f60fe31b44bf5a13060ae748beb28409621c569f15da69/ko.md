```
trsm(side, ul, tA, dA, alpha, A, B)
```

`A*X = alpha*B`의 해를 반환하거나 [`side`](@ref stdlib-blas-side) 및 [`tA`](@ref stdlib-blas-trans)에 의해 결정된 다른 세 가지 변형 중 하나를 반환합니다. 오직 [`ul`](@ref stdlib-blas-uplo) 삼각형만 `A`에서 사용됩니다. [`dA`](@ref stdlib-blas-diag)는 대각선 값이 읽히는지 아니면 모두 1로 가정되는지를 결정합니다.
