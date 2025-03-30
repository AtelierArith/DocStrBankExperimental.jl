```
givens(f::T, g::T, i1::Integer, i2::Integer) where {T} -> (G::Givens, r::T)
```

计算 Givens 旋转 `G` 和标量 `r`，使得对于任何向量 `x`，其中

```
x[i1] = f
x[i2] = g
```

乘法的结果

```
y = G*x
```

具有以下性质

```
y[i1] = r
y[i2] = 0
```

另见 [`LinearAlgebra.Givens`](@ref).
