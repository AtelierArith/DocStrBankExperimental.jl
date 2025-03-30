```
gemmt(uplo, tA, tB, A, B)
```

[`uplo`](@ref stdlib-blas-uplo)에 의해 지정된 `A*B`의 하삼각 또는 상삼각 부분 또는 [`tA`](@ref stdlib-blas-trans) 및 `tB`에 따라 다른 세 가지 변형을 반환합니다.

!!! compat "Julia 1.11"
    `gemmt`는 최소한 Julia 1.11이 필요합니다.

