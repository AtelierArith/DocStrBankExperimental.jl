```
extrema!(r, A)
```

计算 `A` 在 `r` 的单例维度上的最小值和最大值，并将结果写入 `r`。

!!! warning
    当任何被修改的参数与其他参数共享内存时，行为可能会出乎意料。


!!! compat "Julia 1.8"
    此方法需要 Julia 1.8 或更高版本。


# 示例

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> extrema!([(1, 1); (1, 1)], A)
2-element Vector{Tuple{Int64, Int64}}:
 (1, 2)
 (3, 4)

julia> extrema!([(1, 1);; (1, 1)], A)
1×2 Matrix{Tuple{Int64, Int64}}:
 (1, 3)  (2, 4)
```
