```
gemmt!(uplo, tA, tB, alpha, A, B, beta, C)
```

지정된 [`uplo`](@ref stdlib-blas-uplo)에 따라 `C`의 하삼각 또는 상삼각 부분을 `alpha*A*B + beta*C` 또는 [`tA`](@ref stdlib-blas-trans) 및 `tB`에 따라 다른 변형으로 업데이트합니다. 업데이트된 `C`를 반환합니다.

!!! compat "Julia 1.11"
    `gemmt!`는 최소한 Julia 1.11이 필요합니다.

