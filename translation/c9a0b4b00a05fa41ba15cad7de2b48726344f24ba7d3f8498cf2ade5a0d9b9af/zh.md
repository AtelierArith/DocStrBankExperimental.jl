```
reverse(A; dims=:)
```

沿着维度 `dims` 反转 `A`，其中 `dims` 可以是一个整数（单个维度）、一个整数元组（多个维度）或 `:`（沿所有维度反转，默认为此）。另见 [`reverse!`](@ref) 进行就地反转。

# 示例

```jldoctest
julia> b = Int64[1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> reverse(b, dims=2)
2×2 Matrix{Int64}:
 2  1
 4  3

julia> reverse(b)
2×2 Matrix{Int64}:
 4  3
 2  1
```

!!! compat "Julia 1.6"
    在 Julia 1.6 之前，`reverse` 仅支持单个整数 `dims`。

