```
pairs(IndexLinear(), A)
pairs(IndexCartesian(), A)
pairs(IndexStyle(A), A)
```

一个迭代器，用于访问数组 `A` 的每个元素，返回 `i => x`，其中 `i` 是元素的索引，`x = A[i]`。与 `pairs(A)` 相同，不同之处在于可以选择索引的样式。也类似于 `enumerate(A)`，但 `i` 将是 `A` 的有效索引，而 `enumerate` 始终从 1 开始计数，无论 `A` 的索引如何。

指定 [`IndexLinear()`](@ref) 确保 `i` 将是一个整数；指定 [`IndexCartesian()`](@ref) 确保 `i` 将是一个 [`Base.CartesianIndex`](@ref)；指定 `IndexStyle(A)` 选择已定义为数组 `A` 的本地索引样式。

对底层数组的边界进行修改将使此迭代器失效。

# 示例

```jldoctest
julia> A = ["a" "d"; "b" "e"; "c" "f"];

julia> for (index, value) in pairs(IndexStyle(A), A)
           println("$index $value")
       end
1 a
2 b
3 c
4 d
5 e
6 f

julia> S = view(A, 1:2, :);

julia> for (index, value) in pairs(IndexStyle(S), S)
           println("$index $value")
       end
CartesianIndex(1, 1) a
CartesianIndex(2, 1) b
CartesianIndex(1, 2) d
CartesianIndex(2, 2) e
```

另请参见 [`IndexStyle`](@ref)，[`axes`](@ref)。
