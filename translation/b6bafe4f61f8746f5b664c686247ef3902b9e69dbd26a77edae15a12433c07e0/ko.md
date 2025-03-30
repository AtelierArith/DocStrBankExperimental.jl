```
trmv!(ul, tA, dA, A, b)
```

`op(A)*b`를 반환합니다. 여기서 `op`는 [`tA`](@ref stdlib-blas-trans)에 의해 결정됩니다. `A`의 [`ul`](@ref stdlib-blas-uplo) 삼각형만 사용됩니다. [`dA`](@ref stdlib-blas-diag)는 대각선 값이 읽히는지 아니면 모두 1로 가정되는지를 결정합니다. 곱셈은 `b`에서 제자리에서 발생합니다.
