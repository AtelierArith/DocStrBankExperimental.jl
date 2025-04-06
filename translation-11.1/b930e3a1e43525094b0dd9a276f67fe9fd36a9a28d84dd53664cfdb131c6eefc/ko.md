```
gbmv!(trans, m, kl, ku, alpha, A, x, beta, y)
```

벡터 `y`를 `alpha*A*x + beta*y` 또는 `alpha*A'*x + beta*y`로 업데이트합니다. 이는 [`trans`](@ref stdlib-blas-trans)에 따라 다릅니다. 행렬 `A`는 `m` x `size(A,2)` 크기의 일반 밴드 행렬로, `kl` 개의 하삼각 대각선과 `ku` 개의 상삼각 대각선을 가집니다. `alpha`와 `beta`는 스칼라입니다. 업데이트된 `y`를 반환합니다.
