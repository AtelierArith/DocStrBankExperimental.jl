```
resize!(a::Vector, n::Integer) -> Vector
```

将 `a` 调整为包含 `n` 个元素。如果 `n` 小于当前集合长度，则保留前 `n` 个元素。如果 `n` 较大，则新元素不保证被初始化。

# 示例

```jldoctest
julia> resize!([6, 5, 4, 3, 2, 1], 3)
3-element Vector{Int64}:
 6
 5
 4

julia> a = resize!([6, 5, 4, 3, 2, 1], 8);

julia> length(a)
8

julia> a[1:6]
6-element Vector{Int64}:
 6
 5
 4
 3
 2
 1
```
