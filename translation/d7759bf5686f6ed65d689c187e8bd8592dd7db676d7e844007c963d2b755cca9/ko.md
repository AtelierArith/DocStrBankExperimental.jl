```
sbmv!(uplo, k, alpha, A, x, beta, y)
```

벡터 `y`를 `alpha*A*x + beta*y`로 업데이트합니다. 여기서 `A`는 `size(A,2)` 차원의 대칭 밴드 행렬이며, `k`개의 슈퍼 대각선이 인수 `A`에 저장되어 있습니다. `A`의 저장 레이아웃은 [https://www.netlib.org/lapack/explore-html/](https://www.netlib.org/lapack/explore-html/)의 참조 BLAS 모듈, 레벨-2 BLAS에서 설명되어 있습니다. 오직 [`uplo`](@ref stdlib-blas-uplo) 삼각형의 `A`만 사용됩니다.

업데이트된 `y`를 반환합니다.
