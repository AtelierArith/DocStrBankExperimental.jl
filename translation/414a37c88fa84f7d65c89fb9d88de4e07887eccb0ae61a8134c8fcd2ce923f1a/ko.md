```
syrk!(uplo, trans, alpha, A, beta, C)
```

대칭 행렬 `C`의 랭크-k 업데이트를 `alpha*A*transpose(A) + beta*C` 또는 `alpha*transpose(A)*A + beta*C`로 수행합니다. 이는 [`trans`](@ref stdlib-blas-trans)에 따라 다릅니다. 오직 [`uplo`](@ref stdlib-blas-uplo) 삼각형의 `C`만 사용됩니다. `C`를 반환합니다.
