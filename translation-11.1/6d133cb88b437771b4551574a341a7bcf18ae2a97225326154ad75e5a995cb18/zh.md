```
sprandn([rng][,Type],m[,n],p::AbstractFloat)
```

创建一个长度为 `m` 的随机稀疏向量或大小为 `m` x `n` 的稀疏矩阵，具有指定的（独立的）概率 `p`，表示任何条目为非零的概率，其中非零值是从正态分布中抽样的。可选的 `rng` 参数指定一个随机数生成器，参见 [Random Numbers](@ref)。

!!! compat "Julia 1.1"
    指定输出元素类型 `Type` 至少需要 Julia 1.1。


# 示例

```jldoctest; setup = :(using Random; Random.seed!(0))
julia> sprandn(2, 2, 0.75)
2×2 SparseMatrixCSC{Float64, Int64} with 3 stored entries:
 -1.20577     ⋅
  0.311817  -0.234641
```
