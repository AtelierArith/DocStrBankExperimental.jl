```julia
struct OuterProduct{T, ATL<:(AbstractArray{T}), ATR<:(AbstractArray{T})} <: YaoBlocks.LowRankMatrix{T}
```

もし `ATL(R) <: AbstractVector` であれば、外積 `x.left*transpose(x.right)` を表します。そうでなければ、`ATL(R) <: AbstractMatrix` の場合、外積 `x.left*transpose(x.right)` となります。
