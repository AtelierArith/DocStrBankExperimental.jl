```
sparse_hvcat(rows::Tuple{Vararg{Int}}, values...)
```

稀疏的水平和垂直连接在一个调用中。此函数用于块矩阵语法。第一个参数指定每个块行中要连接的参数数量。

!!! compat "Julia 1.8"
    此方法是在 Julia 1.8 中添加的。它模仿了之前的连接行为，其中与来自 LinearAlgebra.jl 的专用“稀疏”矩阵类型的连接在没有任何 SparseArray 参数的情况下自动产生稀疏输出。

