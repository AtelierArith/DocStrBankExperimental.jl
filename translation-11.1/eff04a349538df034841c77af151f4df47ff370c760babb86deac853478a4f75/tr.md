```
givens(A::AbstractArray, i1::Integer, i2::Integer, j::Integer) -> (G::Givens, r)
```

Givens rotasını `G` ve çarpan `r`'yi hesaplar, böylece çarpmanın sonucu

```
B = G*A
```

şu özelliğe sahip olur:

```
B[i1,j] = r
B[i2,j] = 0
```

Ayrıca bkz. [`LinearAlgebra.Givens`](@ref).
