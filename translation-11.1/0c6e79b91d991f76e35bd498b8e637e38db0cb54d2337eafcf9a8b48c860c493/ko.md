```
syrk(uplo, trans, alpha, A)
```

`A`의 상삼각형 또는 하삼각형을 [`uplo`](@ref stdlib-blas-uplo)에 따라 반환하며, `alpha*A*transpose(A)` 또는 `alpha*transpose(A)*A`를 [`trans`](@ref stdlib-blas-trans)에 따라 반환합니다.
