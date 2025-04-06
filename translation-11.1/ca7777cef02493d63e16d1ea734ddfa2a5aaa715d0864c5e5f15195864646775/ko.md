```
trsv!(ul, tA, dA, A, b)
```

`A*x = b`의 해로 `b`를 덮어쓰거나 [`tA`](@ref stdlib-blas-trans) 및 [`ul`](@ref stdlib-blas-uplo)에 의해 결정된 다른 두 변형 중 하나로 덮어씁니다. [`dA`](@ref stdlib-blas-diag)는 대각선 값이 읽히는지 아니면 모두 1로 가정되는지를 결정합니다. 업데이트된 `b`를 반환합니다.
