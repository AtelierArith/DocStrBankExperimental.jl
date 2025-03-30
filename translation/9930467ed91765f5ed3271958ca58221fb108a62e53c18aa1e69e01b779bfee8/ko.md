```
sbmv(uplo, k, alpha, A, x)
```

`alpha*A*x`를 반환합니다. 여기서 `A`는 인수 `A`에 저장된 `k`개의 초대각선을 가진 대칭 밴드 행렬이며, `size(A,2)`의 차수를 가집니다. 오직 [`uplo`](@ref stdlib-blas-uplo) 삼각형의 `A`만 사용됩니다.
