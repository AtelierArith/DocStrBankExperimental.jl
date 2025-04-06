```
hcat(A...)
```

水平连接数组或数字。等价于 [`cat`](@ref)`(A...; dims=2)`，以及语法 `[a b c]` 或 `[a;; b;; c]`。

对于一个大型数组向量，`reduce(hcat, A)` 在 `A isa AbstractVector{<:AbstractVecOrMat}` 时调用高效的方法。对于一个向量的向量，这也可以写作 [`stack`](@ref)`(A)`。

另请参见 [`vcat`](@ref)，[`hvcat`](@ref)。

# 示例

```jldoctest
julia> hcat([1,2], [3,4], [5,6])
2×3 Matrix{Int64}:
 1  3  5
 2  4  6

julia> hcat(1, 2, [30 40], [5, 6, 7]')  # 接受数字
1×7 Matrix{Int64}:
 1  2  30  40  5  6  7

julia> ans == [1 2 [30 40] [5, 6, 7]']  # 相同操作的语法
true

julia> Float32[1 2 [30 40] [5, 6, 7]']  # 提供 eltype 的语法
1×7 Matrix{Float32}:
 1.0  2.0  30.0  40.0  5.0  6.0  7.0

julia> ms = [zeros(2,2), [1 2; 3 4], [50 60; 70 80]];

julia> reduce(hcat, ms)  # 比 hcat(ms...) 更高效
2×6 Matrix{Float64}:
 0.0  0.0  1.0  2.0  50.0  60.0
 0.0  0.0  3.0  4.0  70.0  80.0

julia> stack(ms) |> summary  # 对矩阵的向量不一致
"2×2×3 Array{Float64, 3}"

julia> hcat(Int[], Int[], Int[])  # 空向量，每个大小为 (0,)
0×3 Matrix{Int64}

julia> hcat([1.1, 9.9], Matrix(undef, 2, 0))  # hcat 与空的 2×0 矩阵
2×1 Matrix{Any}:
 1.1
 9.9
```
