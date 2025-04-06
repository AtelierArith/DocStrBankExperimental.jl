```
count([f=identity,] A::AbstractArray; dims=:)
```

计算在给定维度上，`f` 返回 `true` 的 `A` 中元素的数量。

!!! compat "Julia 1.5"
    `dims` 关键字是在 Julia 1.5 中添加的。


!!! compat "Julia 1.6"
    `init` 关键字是在 Julia 1.6 中添加的。


# 示例

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> count(<=(2), A, dims=1)
1×2 Matrix{Int64}:
 1  1

julia> count(<=(2), A, dims=2)
2×1 Matrix{Int64}:
 2
 0
```
