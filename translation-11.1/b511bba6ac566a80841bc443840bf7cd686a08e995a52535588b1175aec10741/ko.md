```
her2k!(uplo, trans, alpha, A, B, beta, C)
```

Hermitian 행렬 `C`의 Rank-2k 업데이트는 `alpha*A*B' + alpha*B*A' + beta*C` 또는 `alpha*A'*B + alpha*B'*A + beta*C`로 [`trans`](@ref stdlib-blas-trans)에 따라 수행됩니다. 스칼라 `beta`는 실수여야 합니다. `C`의 [`uplo`](@ref stdlib-blas-uplo) 삼각형만 사용됩니다. `C`를 반환합니다.
