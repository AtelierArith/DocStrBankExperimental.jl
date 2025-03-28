```
trmv(ul, tA, dA, A, b)
```

Retourne `op(A)*b`, où `op` est déterminé par [`tA`](@ref stdlib-blas-trans). Seule la triangle [`ul`](@ref stdlib-blas-uplo) de `A` est utilisée. [`dA`](@ref stdlib-blas-diag) détermine si les valeurs diagonales sont lues ou supposées être toutes égales à un.
