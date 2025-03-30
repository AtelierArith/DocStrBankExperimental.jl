```
herk!(uplo, trans, alpha, A, beta, C)
```

복소 배열에 대해서만 메서드가 제공됩니다. Hermitian 행렬 `C`의 랭크-k 업데이트는 [`trans`](@ref stdlib-blas-trans)에 따라 `alpha*A*A' + beta*C` 또는 `alpha*A'*A + beta*C`로 수행됩니다. 오직 [`uplo`](@ref stdlib-blas-uplo) 삼각형의 `C`만 업데이트됩니다. `C`를 반환합니다.
