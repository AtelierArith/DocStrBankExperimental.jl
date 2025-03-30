```
sortslices(A; dims, alg::Algorithm=DEFAULT_UNSTABLE, lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

对数组 `A` 的切片进行排序。必需的关键字参数 `dims` 必须是一个整数或整数元组。它指定了切片排序的维度。

例如，如果 `A` 是一个矩阵，`dims=1` 将排序行，`dims=2` 将排序列。请注意，默认的比较函数在一维切片上是按字典序排序的。

有关其余关键字参数，请参见 [`sort!`](@ref) 的文档。

# 示例

```jldoctest
julia> sortslices([7 3 5; -1 6 4; 9 -2 8], dims=1) # 排序行
3×3 Matrix{Int64}:
 -1   6  4
  7   3  5
  9  -2  8

julia> sortslices([7 3 5; -1 6 4; 9 -2 8], dims=1, lt=(x,y)->isless(x[2],y[2]))
3×3 Matrix{Int64}:
  9  -2  8
  7   3  5
 -1   6  4

julia> sortslices([7 3 5; -1 6 4; 9 -2 8], dims=1, rev=true)
3×3 Matrix{Int64}:
  9  -2  8
  7   3  5
 -1   6  4

julia> sortslices([7 3 5; 6 -1 -4; 9 -2 8], dims=2) # 排序列
3×3 Matrix{Int64}:
  3   5  7
 -1  -4  6
 -2   8  9

julia> sortslices([7 3 5; 6 -1 -4; 9 -2 8], dims=2, alg=InsertionSort, lt=(x,y)->isless(x[2],y[2]))
3×3 Matrix{Int64}:
  5   3  7
 -4  -1  6
  8  -2  9

julia> sortslices([7 3 5; 6 -1 -4; 9 -2 8], dims=2, rev=true)
3×3 Matrix{Int64}:
 7   5   3
 6  -4  -1
 9   8  -2
```

# 更高维度

`sortslices` 自然扩展到更高维度。例如，如果 `A` 是一个 2x2x2 的数组，`sortslices(A, dims=3)` 将在第 3 维度内排序切片，将 2x2 的切片 `A[:, :, 1]` 和 `A[:, :, 2]` 传递给比较函数。请注意，虽然在高维切片上没有默认顺序，但您可以使用 `by` 或 `lt` 关键字参数来指定这样的顺序。

如果 `dims` 是一个元组，则 `dims` 中维度的顺序是相关的，并指定切片的线性顺序。例如，如果 `A` 是三维的，`dims` 是 `(1, 2)`，则前两个维度的顺序被重新排列，以便对剩余的第三维度的切片进行排序。如果 `dims` 是 `(2, 1)`，则将取相同的切片，但结果顺序将是行优先的。

# 更高维度示例

```
julia> A = [4 3; 2 1 ;;; 'A' 'B'; 'C' 'D']
2×2×2 Array{Any, 3}:
[:, :, 1] =
 4  3
 2  1

[:, :, 2] =
 'A'  'B'
 'C'  'D'

julia> sortslices(A, dims=(1,2))
2×2×2 Array{Any, 3}:
[:, :, 1] =
 1  3
 2  4

[:, :, 2] =
 'D'  'B'
 'C'  'A'

julia> sortslices(A, dims=(2,1))
2×2×2 Array{Any, 3}:
[:, :, 1] =
 1  2
 3  4

[:, :, 2] =
 'D'  'C'
 'B'  'A'

julia> sortslices(reshape([5; 4; 3; 2; 1], (1,1,5)), dims=3, by=x->x[1,1])
1×1×5 Array{Int64, 3}:
[:, :, 1] =
 1

[:, :, 2] =
 2

[:, :, 3] =
 3

[:, :, 4] =
 4

[:, :, 5] =
 5
```
