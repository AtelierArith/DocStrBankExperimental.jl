```
strides(A)
```

返回每个维度的内存步幅元组。

另见：[`stride`](@ref)。

# 示例

```jldoctest
julia> A = fill(1, (3,4,5));

julia> strides(A)
(1, 3, 12)
```
