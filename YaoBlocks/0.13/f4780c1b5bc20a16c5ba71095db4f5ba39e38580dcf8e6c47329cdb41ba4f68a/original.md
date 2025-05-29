```julia
struct OuterProduct{T, ATL<:(AbstractArray{T}), ATR<:(AbstractArray{T})} <: YaoBlocks.LowRankMatrix{T}
```

If `ATL(R) <: AbstractVector`, it represents an outer product `x.left*transpose(x.right)`. Else if `ATL(R) <: AbstractMatrix`, then it is an outer product `x.left*transpose(x.right)`.
