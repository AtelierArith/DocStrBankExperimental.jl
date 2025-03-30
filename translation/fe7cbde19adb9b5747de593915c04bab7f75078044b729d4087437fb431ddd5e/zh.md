```
VecOrMat{T}
```

联合类型 [`Vector{T}`](@ref) 和 [`Matrix{T}`](@ref)，允许函数接受矩阵或向量。

# 示例

```jldoctest
julia> Vector{Float64} <: VecOrMat{Float64}
true

julia> Matrix{Float64} <: VecOrMat{Float64}
true

julia> Array{Float64, 3} <: VecOrMat{Float64}
false
```
