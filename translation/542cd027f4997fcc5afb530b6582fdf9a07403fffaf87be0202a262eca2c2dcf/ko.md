```
syr2k(uplo, trans, A, B)
```

[`uplo`](@ref stdlib-blas-uplo) 삼각형을 반환합니다 `A*transpose(B) + B*transpose(A)` 또는 `transpose(A)*B + transpose(B)*A`, [`trans`](@ref stdlib-blas-trans)에 따라.
