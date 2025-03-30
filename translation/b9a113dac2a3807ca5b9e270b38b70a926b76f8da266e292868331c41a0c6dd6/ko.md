```
syr!(uplo, alpha, x, A)
```

대칭 행렬 `A`의 랭크-1 업데이트로, 벡터 `x`를 사용하여 `alpha*x*transpose(x) + A`로 업데이트합니다. [`uplo`](@ref stdlib-blas-uplo)는 업데이트할 `A`의 삼각형을 제어합니다. `A`를 반환합니다.
