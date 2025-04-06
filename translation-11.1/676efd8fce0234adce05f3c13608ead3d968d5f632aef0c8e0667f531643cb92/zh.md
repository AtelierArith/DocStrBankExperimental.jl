```
stack(iter; [dims])
```

将大小相等的数组（或其他可迭代对象）集合组合成一个更大的数组，通过沿一个或多个新维度排列它们。

默认情况下，元素的轴首先被放置，给出 `size(result) = (size(first(iter))..., size(iter)...)`。这与 [`Iterators.flatten`](@ref)`(iter)` 的元素顺序相同。

使用关键字 `dims::Integer`，则 `iter` 的第 `i` 个元素变为切片 [`selectdim`](@ref)`(result, dims, i)`，使得 `size(result, dims) == length(iter)`。在这种情况下，`stack` 反转了 [`eachslice`](@ref) 的作用，使用相同的 `dims`。

各种 [`cat`](@ref) 函数也组合数组。然而，这些函数扩展了数组现有的（可能是微不足道的）维度，而不是将数组放置在新维度上。它们还接受作为单独参数的数组，而不是单个集合。

!!! compat "Julia 1.9"
    此函数至少需要 Julia 1.9。


# 示例

```jldoctest
julia> vecs = (1:2, [30, 40], Float32[500, 600]);

julia> mat = stack(vecs)
2×3 Matrix{Float32}:
 1.0  30.0  500.0
 2.0  40.0  600.0

julia> mat == hcat(vecs...) == reduce(hcat, collect(vecs))
true

julia> vec(mat) == vcat(vecs...) == reduce(vcat, collect(vecs))
true

julia> stack(zip(1:4, 10:99))  # 接受任何迭代器的迭代器
2×4 Matrix{Int64}:
  1   2   3   4
 10  11  12  13

julia> vec(ans) == collect(Iterators.flatten(zip(1:4, 10:99)))
true

julia> stack(vecs; dims=1)  # 与任何 cat 函数不同，vecs[1] 的第 1 轴是结果的第 2 轴
3×2 Matrix{Float32}:
   1.0    2.0
  30.0   40.0
 500.0  600.0

julia> x = rand(3,4);

julia> x == stack(eachcol(x)) == stack(eachrow(x), dims=1)  # eachslice 的逆
true
```

更高维度的示例：

```jldoctest
julia> A = rand(5, 7, 11);

julia> E = eachslice(A, dims=2);  # 一个矩阵的向量

julia> (element = size(first(E)), container = size(E))
(element = (5, 11), container = (7,))

julia> stack(E) |> size
(5, 11, 7)

julia> stack(E) == stack(E; dims=3) == cat(E...; dims=3)
true

julia> A == stack(E; dims=2)
true

julia> M = (fill(10i+j, 2, 3) for i in 1:5, j in 1:7);

julia> (element = size(first(M)), container = size(M))
(element = (2, 3), container = (5, 7))

julia> stack(M) |> size  # 保持所有维度
(2, 3, 5, 7)

julia> stack(M; dims=1) |> size  # vec(container) 沿 dims=1
(35, 2, 3)

julia> hvcat(5, M...) |> size  # hvcat 将矩阵放在一起
(14, 15)
```
