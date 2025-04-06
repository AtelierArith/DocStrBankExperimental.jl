```
parent(A)
```

返回视图的基础父对象。类型为 `SubArray`、`SubString`、`ReshapedArray` 或 `LinearAlgebra.Transpose` 的对象的父对象是创建对象时传递给 `view`、`reshape`、`transpose` 等的参数。如果输入不是一个包装对象，则返回输入本身。如果输入被多次包装，则只会移除最外层的包装。

# 示例

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> V = view(A, 1:2, :)
2×2 view(::Matrix{Int64}, 1:2, :) with eltype Int64:
 1  2
 3  4

julia> parent(V)
2×2 Matrix{Int64}:
 1  2
 3  4
```
