```
syr2k(uplo, trans, alpha, A, B)
```

`alpha*A*transpose(B) + alpha*B*transpose(A)` 또는 `alpha*transpose(A)*B + alpha*transpose(B)*A`의 [`uplo`](@ref stdlib-blas-uplo) 삼각형을 반환합니다. 이는 [`trans`](@ref stdlib-blas-trans)에 따라 다릅니다.
