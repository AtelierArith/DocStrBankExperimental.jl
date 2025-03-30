```
givens(A::AbstractArray, i1::Integer, i2::Integer, j::Integer) -> (G::Givens, r)
```

计算 Givens 旋转 `G` 和标量 `r`，使得乘法的结果

```
B = G*A
```

具有以下属性：

```
B[i1,j] = r
B[i2,j] = 0
```

另见 [`LinearAlgebra.Givens`](@ref). ```
