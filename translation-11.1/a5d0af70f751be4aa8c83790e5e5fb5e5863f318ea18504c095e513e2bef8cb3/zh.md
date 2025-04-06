```
nullspace(M; atol::Real=0, rtol::Real=atol>0 ? 0 : n*ϵ)
nullspace(M, rtol::Real) = nullspace(M; rtol=rtol) # 在 Julia 2.0 中将被弃用

通过包括 `M` 的奇异向量来计算 `M` 的零空间的基，这些奇异向量的奇异值的绝对值小于 `max(atol, rtol*σ₁)`，其中 `σ₁` 是 `M` 的最大奇异值。

默认情况下，相对容忍度 `rtol` 是 `n*ϵ`，其中 `n` 是 `M` 最小维度的大小，`ϵ` 是 `M` 的元素类型的 [`eps`](@ref)。

# 示例

```

jldoctest julia> M = [1 0 0; 0 1 0; 0 0 0] 3×3 Matrix{Int64}:  1  0  0  0  1  0  0  0  0

julia> nullspace(M) 3×1 Matrix{Float64}:  0.0  0.0  1.0

julia> nullspace(M, rtol=3) 3×3 Matrix{Float64}:  0.0  1.0  0.0  1.0  0.0  0.0  0.0  0.0  1.0

julia> nullspace(M, atol=0.95) 3×1 Matrix{Float64}:  0.0  0.0  1.0 ```
