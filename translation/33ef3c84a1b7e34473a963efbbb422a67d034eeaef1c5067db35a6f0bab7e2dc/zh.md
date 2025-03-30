```
cat(A...; dims)
```

沿着 `dims` 指定的维度连接输入数组。

在维度 `d in dims` 上，输出数组的大小为 `sum(size(a,d) for a in A)`。在其他维度上，所有输入数组的大小应相同，这也将是输出数组在这些维度上的大小。

如果 `dims` 是一个单一数字，则不同的数组在该维度上紧密打包。如果 `dims` 是一个包含多个维度的可迭代对象，则沿着这些维度的位置会同时增加，每个输入数组填充其他地方为零。这允许构造块对角矩阵，如 `cat(matrices...; dims=(1,2))`，以及它们的高维类比。

特殊情况 `dims=1` 是 [`vcat`](@ref)，`dims=2` 是 [`hcat`](@ref)。另见 [`hvcat`](@ref)，[`hvncat`](@ref)，[`stack`](@ref)，[`repeat`](@ref)。

关键字还接受 `Val(dims)`。

!!! compat "Julia 1.8"
    对于多个维度，`dims = Val(::Tuple)` 是在 Julia 1.8 中添加的。


# 示例

在不同维度中连接两个数组：

```jldoctest
julia> a = [1 2 3]
1×3 Matrix{Int64}:
 1  2  3

julia> b = [4 5 6]
1×3 Matrix{Int64}:
 4  5  6

julia> cat(a, b; dims=1)
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> cat(a, b; dims=2)
1×6 Matrix{Int64}:
 1  2  3  4  5  6

julia> cat(a, b; dims=(1, 2))
2×6 Matrix{Int64}:
 1  2  3  0  0  0
 0  0  0  4  5  6
```

# 扩展帮助

连接 3D 数组：

```jldoctest
julia> a = ones(2, 2, 3);

julia> b = ones(2, 2, 4);

julia> c = cat(a, b; dims=3);

julia> size(c) == (2, 2, 7)
true
```

连接不同大小的数组：

```jldoctest
julia> cat([1 2; 3 4], [pi, pi], fill(10, 2,3,1); dims=2)  # 同 hcat
2×6×1 Array{Float64, 3}:
[:, :, 1] =
 1.0  2.0  3.14159  10.0  10.0  10.0
 3.0  4.0  3.14159  10.0  10.0  10.0
```

构造一个块对角矩阵：

```
julia> cat(true, trues(2,2), trues(4)', dims=(1,2))  # 块对角
4×7 Matrix{Bool}:
 1  0  0  0  0  0  0
 0  1  1  0  0  0  0
 0  1  1  0  0  0  0
 0  0  0  1  1  1  1
```

```
julia> cat(1, [2], [3;;]; dims=Val(2))
1×3 Matrix{Int64}:
 1  2  3
```

!!! note
    `cat` 不会连接两个字符串，你可能想使用 `*`。


```jldoctest
julia> a = "aaa";

julia> b = "bbb";

julia> cat(a, b; dims=1)
2-element Vector{String}:
 "aaa"
 "bbb"

julia> cat(a, b; dims=2)
1×2 Matrix{String}:
 "aaa"  "bbb"

julia> a * b
"aaabbb"
```
