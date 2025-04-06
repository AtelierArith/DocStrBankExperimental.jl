```
herk(uplo, trans, alpha, A)
```

복소 배열에 대해서만 메서드가 있습니다. [`trans`](@ref stdlib-blas-trans)에 따라 `alpha*A*A'` 또는 `alpha*A'*A`의 [`uplo`](@ref stdlib-blas-uplo) 삼각형을 반환합니다.
