```
hemv!(ul, alpha, A, x, beta, y)
```

벡터 `y`를 `alpha*A*x + beta*y`로 업데이트합니다. `A`는 에르미트 행렬로 가정됩니다. `A`의 [`ul`](@ref stdlib-blas-uplo) 삼각형만 사용됩니다. `alpha`와 `beta`는 스칼라입니다. 업데이트된 `y`를 반환합니다.
