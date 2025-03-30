```
syr2k!(uplo, trans, alpha, A, B, beta, C)
```

대칭 행렬 `C`의 Rank-2k 업데이트는 `alpha*A*transpose(B) + alpha*B*transpose(A) + beta*C` 또는 `alpha*transpose(A)*B + alpha*transpose(B)*A + beta*C`로 [`trans`](@ref stdlib-blas-trans)에 따라 수행됩니다. 오직 [`uplo`](@ref stdlib-blas-uplo) 삼각형의 `C`만 사용됩니다. `C`를 반환합니다.
