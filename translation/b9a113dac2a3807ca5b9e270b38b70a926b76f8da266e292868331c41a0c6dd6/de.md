```
syr!(uplo, alpha, x, A)
```

Rank-1-Aktualisierung der symmetrischen Matrix `A` mit dem Vektor `x` als `alpha*x*transpose(x) + A`. [`uplo`](@ref stdlib-blas-uplo) steuert, welches Dreieck von `A` aktualisiert wird. Gibt `A` zurück.
