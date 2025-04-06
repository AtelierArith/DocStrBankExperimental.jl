```
sparse_vcat(A...)
```

沿着维度 1 连接。返回一个 SparseMatrixCSC 对象。

!!! compat "Julia 1.8"
    此方法是在 Julia 1.8 中添加的。它模仿了之前的连接行为，其中与来自 LinearAlgebra.jl 的专用 "稀疏" 矩阵类型的连接即使在没有任何 SparseArray 参数的情况下也会自动产生稀疏输出。

