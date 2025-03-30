```
length(A::AbstractArray)
```

返回数组中的元素数量，默认为 `prod(size(A))`。

# 示例

```jldoctest
julia> length([1, 2, 3, 4])
4

julia> length([1 2; 3 4])
4
```
