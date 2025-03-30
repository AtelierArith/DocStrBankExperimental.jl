```
cumsum(A; dims::Integer)
```

沿着维度 `dims` 的累积和。另请参见 [`cumsum!`](@ref)，以使用预分配的输出数组，既可以提高性能，也可以控制输出的精度（例如，避免溢出）。

# 示例

```jldoctest
julia> a = [1 2 3; 4 5 6]
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> cumsum(a, dims=1)
2×3 Matrix{Int64}:
 1  2  3
 5  7  9

julia> cumsum(a, dims=2)
2×3 Matrix{Int64}:
 1  3   6
 4  9  15
```

!!! note
    返回数组的 `eltype` 对于小于系统字大小的有符号整数为 `Int`，对于小于系统字大小的无符号整数为 `UInt`。为了保留小有符号或无符号整数数组的 `eltype`，应使用 `accumulate(+, A)`。

    ```jldoctest
    julia> cumsum(Int8[100, 28])
    2-element Vector{Int64}:
     100
     128

    julia> accumulate(+,Int8[100, 28])
    2-element Vector{Int8}:
      100
     -128
    ```

    在前一种情况下，整数被扩展到系统字大小，因此结果为 `Int64[100, 128]`。在后一种情况下，没有发生这样的扩展，整数溢出导致结果为 `Int8[100, -128]`。

