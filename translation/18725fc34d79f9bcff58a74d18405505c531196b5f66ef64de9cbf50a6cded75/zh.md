```
view(A, inds...)
```

像 [`getindex`](@ref) 一样，但返回一个轻量级数组，该数组懒惰地引用（或有效地是对）父数组 `A` 在给定索引或索引 `inds` 处的视图，而不是急切地提取元素或构造一个复制的子集。对返回值（通常是 [`SubArray`](@ref)）调用 [`getindex`](@ref) 或 [`setindex!`](@ref) 会动态计算访问或修改父数组的索引。如果在调用 `view` 之后更改父数组的形状，则行为是未定义的，因为对父数组没有边界检查；例如，这可能会导致段错误。

一些不可变的父数组（如范围）可能会选择在某些情况下简单地重新计算一个新数组，而不是返回 `SubArray`，如果这样做是高效的并且提供兼容的语义。

!!! compat "Julia 1.6"
    在 Julia 1.6 或更高版本中，可以在 `AbstractString` 上调用 `view`，返回一个 `SubString`。


# 示例

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> b = view(A, :, 1)
2-element view(::Matrix{Int64}, :, 1) with eltype Int64:
 1
 3

julia> fill!(b, 0)
2-element view(::Matrix{Int64}, :, 1) with eltype Int64:
 0
 0

julia> A # 注意 A 已经改变，即使我们修改了 b
2×2 Matrix{Int64}:
 0  2
 0  4

julia> view(2:5, 2:3) # 返回一个范围，因为类型是不可变的
3:4
```
