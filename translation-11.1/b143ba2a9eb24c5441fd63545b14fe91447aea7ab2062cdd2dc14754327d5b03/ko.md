```
hemm(side, ul, alpha, A, B)
```

`alpha*A*B` 또는 `alpha*B*A`를 [`side`](@ref stdlib-blas-side)에 따라 반환합니다. `A`는 에르미트 행렬로 가정됩니다. `A`의 [`ul`](@ref stdlib-blas-uplo) 삼각형만 사용됩니다.
