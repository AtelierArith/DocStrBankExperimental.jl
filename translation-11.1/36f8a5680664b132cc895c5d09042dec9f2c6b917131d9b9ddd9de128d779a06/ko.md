```
gbmv(trans, m, kl, ku, alpha, A, x)
```

[`trans`](@ref stdlib-blas-trans)에 따라 `alpha*A*x` 또는 `alpha*A'*x`를 반환합니다. 행렬 `A`는 `kl`개의 하삼각 대각선과 `ku`개의 상삼각 대각선을 가진 `m` x `size(A,2)` 차원의 일반 밴드 행렬이며, `alpha`는 스칼라입니다.
