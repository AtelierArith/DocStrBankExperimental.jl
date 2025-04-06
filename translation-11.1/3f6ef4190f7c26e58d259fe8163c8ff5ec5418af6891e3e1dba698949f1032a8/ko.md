```
gemm!(tA, tB, alpha, A, B, beta, C)
```

`C`를 `alpha*A*B + beta*C`로 업데이트하거나 [`tA`](@ref stdlib-blas-trans) 및 `tB`에 따라 다른 세 가지 변형으로 업데이트합니다. 업데이트된 `C`를 반환합니다.
