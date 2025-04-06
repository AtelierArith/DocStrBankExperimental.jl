```
her!(uplo, alpha, x, A)
```

복소 배열에 대해서만 사용 가능한 메서드입니다. Hermitian 행렬 `A`의 랭크-1 업데이트로 벡터 `x`를 사용하여 `alpha*x*x' + A`를 계산합니다. [`uplo`](@ref stdlib-blas-uplo)는 업데이트할 `A`의 삼각형을 제어합니다. `A`를 반환합니다.
