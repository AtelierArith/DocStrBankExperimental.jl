```
repeat(A::AbstractArray; inner=ntuple(Returns(1), ndims(A)), outer=ntuple(Returns(1), ndims(A)))
```

通过重复 `A` 的条目构造一个数组。`inner` 的第 i 个元素指定 `A` 的第 i 个维度的单个条目应重复的次数。`outer` 的第 i 个元素指定沿 `A` 的第 i 个维度的切片应重复的次数。如果省略 `inner` 或 `outer`，则不执行重复。

# 示例

```jldoctest
julia> repeat(1:2, inner=2)
4-element Vector{Int64}:
 1
 1
 2
 2

julia> repeat(1:2, outer=2)
4-element Vector{Int64}:
 1
 2
 1
 2

julia> repeat([1 2; 3 4], inner=(2, 1), outer=(1, 3))
4×6 Matrix{Int64}:
 1  2  1  2  1  2
 1  2  1  2  1  2
 3  4  3  4  3  4
 3  4  3  4  3  4
```
