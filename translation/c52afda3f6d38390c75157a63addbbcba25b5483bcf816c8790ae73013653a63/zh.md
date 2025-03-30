```
similar(A::AbstractSparseMatrixCSC{Tv,Ti}, [::Type{TvNew}, ::Type{TiNew}, m::Integer, n::Integer]) where {Tv,Ti}
```

创建一个未初始化的可变数组，具有给定的元素类型、索引类型和大小，基于给定的源 `SparseMatrixCSC`。新的稀疏矩阵保持原始稀疏矩阵的结构，除非输出矩阵的维度与输出不同。

输出矩阵在与输入相同的位置上有零，但在非零位置上有未初始化的值。
