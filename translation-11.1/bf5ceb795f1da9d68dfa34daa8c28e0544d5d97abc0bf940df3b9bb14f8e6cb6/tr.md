```
givens(x::AbstractVector, i1::Integer, i2::Integer) -> (G::Givens, r)
```

Givens rotasını `G` ve çarpan `r`'yi hesaplar, böylece çarpmanın sonucu

```
B = G*x
```

şu özelliğe sahip olur:

```
B[i1] = r
B[i2] = 0
```

Ayrıca bkz. [`LinearAlgebra.Givens`](@ref).
