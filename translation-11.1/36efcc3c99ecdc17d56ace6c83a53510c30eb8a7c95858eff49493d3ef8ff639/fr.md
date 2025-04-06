```
trsv(ul, tA, dA, A, b)
```

Retourne la solution de `A*x = b` ou l'une des deux autres variantes déterminées par [`tA`](@ref stdlib-blas-trans) et [`ul`](@ref stdlib-blas-uplo). [`dA`](@ref stdlib-blas-diag) détermine si les valeurs diagonales sont lues ou supposées être toutes égales à un.
