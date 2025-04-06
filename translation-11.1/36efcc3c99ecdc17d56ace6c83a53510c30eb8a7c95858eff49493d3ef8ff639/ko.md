```
trsv(ul, tA, dA, A, b)
```

`A*x = b`의 해를 반환하거나 [`tA`](@ref stdlib-blas-trans) 및 [`ul`](@ref stdlib-blas-uplo)에 의해 결정된 다른 두 변형 중 하나를 반환합니다. [`dA`](@ref stdlib-blas-diag)는 대각선 값이 읽히는지 아니면 모두 1로 가정되는지를 결정합니다.
