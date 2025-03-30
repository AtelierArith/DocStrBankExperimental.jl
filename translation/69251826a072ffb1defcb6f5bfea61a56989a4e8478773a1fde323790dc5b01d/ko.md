```
gemv!(tA, alpha, A, x, beta, y)
```

벡터 `y`를 `alpha*A*x + beta*y` 또는 `alpha*A'x + beta*y`로 업데이트합니다. [`tA`](@ref stdlib-blas-trans)에 따라 다릅니다. `alpha`와 `beta`는 스칼라입니다. 업데이트된 `y`를 반환합니다.
