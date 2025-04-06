```
maximum!(r, A)
```

计算 `A` 在 `r` 的单例维度上的最大值，并将结果写入 `r`。

!!! warning
    当任何被修改的参数与其他参数共享内存时，行为可能会出乎意料。


# 示例

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> maximum!([1; 1], A)
2-element Vector{Int64}:
 2
 4

julia> maximum!([1 1], A)
1×2 Matrix{Int64}:
 3  4
```
