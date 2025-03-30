```
sprand([rng],[T::Type],m,[n],p::AbstractFloat)
sprand([rng],m,[n],p::AbstractFloat,[rfn=rand])
```

创建一个随机长度为 `m` 的稀疏向量或 `m` x `n` 的稀疏矩阵，其中任何元素为非零的概率独立地由 `p` 给出（因此非零的平均密度也恰好为 `p`）。可选的 `rng` 参数指定一个随机数生成器，参见 [Random Numbers](@ref)。可选的 `T` 参数指定元素类型，默认为 `Float64`。

默认情况下，非零值是从均匀分布中采样的，使用 [`rand`](@ref) 函数，即通过 `rand(T)`，或者如果提供了 `rng`，则为 `rand(rng, T)`；对于默认的 `T=Float64`，这对应于在 `[0,1)` 中均匀采样的非零值。

您可以通过传递自定义的 `rfn` 函数来从不同的分布中采样非零值，而不是使用 `rand`。这应该是一个函数 `rfn(k)`，返回一个包含 `k` 个从所需分布中采样的随机数的数组；或者，如果提供了 `rng`，则应该是一个函数 `rfn(rng, k)`。

# 示例

```jldoctest; setup = :(using Random; Random.seed!(1234))
julia> sprand(Bool, 2, 2, 0.5)
2×2 SparseMatrixCSC{Bool, Int64} with 2 stored entries:
 1  1
 ⋅  ⋅

julia> sprand(Float64, 3, 0.75)
3-element SparseVector{Float64, Int64} with 2 stored entries:
  [1]  =  0.795547
  [2]  =  0.49425
```
