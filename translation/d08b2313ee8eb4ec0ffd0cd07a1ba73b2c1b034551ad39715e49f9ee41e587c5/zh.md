```
stride(A, k::Integer)
```

返回在维度 `k` 中相邻元素之间的内存距离（以元素数量为单位）。

另见: [`strides`](@ref)。

# 示例

```jldoctest
julia> A = fill(1, (3,4,5));

julia> stride(A,2)
3

julia> stride(A,3)
12
```
