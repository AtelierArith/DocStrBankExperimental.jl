```
hemm!(side, ul, alpha, A, B, beta, C)
```

`C`를 `alpha*A*B + beta*C` 또는 `alpha*B*A + beta*C`로 업데이트합니다. 이는 [`side`](@ref stdlib-blas-side)에 따라 다릅니다. `A`는 에르미트 행렬로 가정됩니다. `A`의 [`ul`](@ref stdlib-blas-uplo) 삼각형만 사용됩니다. 업데이트된 `C`를 반환합니다.
