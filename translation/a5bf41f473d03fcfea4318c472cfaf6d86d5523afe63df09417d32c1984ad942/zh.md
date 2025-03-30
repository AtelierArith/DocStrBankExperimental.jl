```
partialsort!(v, k; by=identity, lt=isless, rev=false)
```

部分地对向量 `v` 进行就地排序，使得索引 `k` 处的值（如果 `k` 是一个范围，则为相邻值的范围）出现在如果数组完全排序时应该出现的位置。如果 `k` 是单个索引，则返回该值；如果 `k` 是一个范围，则返回这些索引处的值的数组。请注意，`partialsort!` 可能不会完全排序输入数组。

有关关键字参数，请参见 [`sort!`](@ref) 的文档。

# 示例

```jldoctest
julia> a = [1, 2, 4, 3, 4]
5-element Vector{Int64}:
 1
 2
 4
 3
 4

julia> partialsort!(a, 4)
4

julia> a
5-element Vector{Int64}:
 1
 2
 3
 4
 4

julia> a = [1, 2, 4, 3, 4]
5-element Vector{Int64}:
 1
 2
 4
 3
 4

julia> partialsort!(a, 4, rev=true)
2

julia> a
5-element Vector{Int64}:
 4
 4
 3
 2
 1
```
