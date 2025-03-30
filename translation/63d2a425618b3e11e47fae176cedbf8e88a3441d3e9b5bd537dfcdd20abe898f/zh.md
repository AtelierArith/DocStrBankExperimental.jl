```
cumprod(A; dims::Integer)
```

沿着维度 `dim` 的累积乘积。另请参见 [`cumprod!`](@ref)，以使用预分配的输出数组，这样可以提高性能并控制输出的精度（例如，避免溢出）。

# 示例

```jldoctest
julia> a = Int8[1 2 3; 4 5 6];

julia> cumprod(a, dims=1)
2×3 Matrix{Int64}:
 1   2   3
 4  10  18

julia> cumprod(a, dims=2)
2×3 Matrix{Int64}:
 1   2    6
 4  20  120
```
