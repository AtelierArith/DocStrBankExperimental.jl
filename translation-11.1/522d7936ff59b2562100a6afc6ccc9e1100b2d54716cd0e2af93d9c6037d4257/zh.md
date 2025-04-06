```
accumulate(op, A; dims::Integer, [init])
```

沿着 `A` 的维度 `dims` 进行累积操作 `op`（对于向量，提供 `dims` 是可选的）。可以通过关键字参数可选地提供初始值 `init`。另请参见 [`accumulate!`](@ref)，以使用预分配的输出数组，这样可以提高性能并控制输出的精度（例如，避免溢出）。

对于常见操作，有 `accumulate` 的专用变体，见 [`cumsum`](@ref)，[`cumprod`](@ref)。有关懒惰版本，请参见 [`Iterators.accumulate`](@ref)。

!!! compat "Julia 1.5"
    在非数组迭代器上使用 `accumulate` 至少需要 Julia 1.5。


# 示例

```jldoctest
julia> accumulate(+, [1,2,3])
3-element Vector{Int64}:
 1
 3
 6

julia> accumulate(min, (1, -2, 3, -4, 5), init=0)
(0, -2, -2, -4, -4)

julia> accumulate(/, (2, 4, Inf), init=100)
(50.0, 12.5, 0.0)

julia> accumulate(=>, i^2 for i in 1:3)
3-element Vector{Any}:
          1
        1 => 4
 (1 => 4) => 9

julia> accumulate(+, fill(1, 3, 4))
3×4 Matrix{Int64}:
 1  4  7  10
 2  5  8  11
 3  6  9  12

julia> accumulate(+, fill(1, 2, 5), dims=2, init=100.0)
2×5 Matrix{Float64}:
 101.0  102.0  103.0  104.0  105.0
 101.0  102.0  103.0  104.0  105.0
```
