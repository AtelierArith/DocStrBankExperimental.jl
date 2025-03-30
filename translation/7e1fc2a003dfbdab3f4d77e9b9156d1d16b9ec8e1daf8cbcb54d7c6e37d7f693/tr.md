```
givens(f::T, g::T, i1::Integer, i2::Integer) where {T} -> (G::Givens, r::T)
```

Givens rotasını `G` ve herhangi bir vektör `x` için

```
x[i1] = f
x[i2] = g
```

şu şekilde hesaplar:

```
y = G*x
```

sonucunun şu özelliğe sahip olmasını sağlar:

```
y[i1] = r
y[i2] = 0
```

Ayrıca bkz. [`LinearAlgebra.Givens`](@ref).
