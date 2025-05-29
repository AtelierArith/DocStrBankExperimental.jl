```
XPRSrhssa(prob, nrows, rowind, lower, upper)::lower, upper
```

指定された右辺（RHS）関数係数の上限および下限の感度範囲を返します。

これらの範囲内でRHS係数が変動しても、現在の基準は最適のままであり、削減コストは有効のままです。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `nrows::Integer`: 感度範囲が必要なRHS係数の数。
  * `rowind::AbstractVector{Integer}`: 感度範囲が必要なRHS係数の行のインデックスを含む長さ`nrows`の整数配列。
  * `lower::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: RHSの下限範囲値が返される長さ`nrows`の倍精度配列。適切なサイズの配列を関数に割り当てさせるために、この引数に`XPRS_ALLOC`を渡すことができます。この情報を照会しないために、この引数に`nothing`を渡すこともできます。
  * `upper::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: RHSの上限範囲値が返される長さ`nrows`の倍精度配列。適切なサイズの配列を関数に割り当てさせるために、この引数に`XPRS_ALLOC`を渡すことができます。この情報を照会しないために、この引数に`nothing`を渡すこともできます。

# 戻り値

  * `lower::Union{Nothing,AbstractVector{Float64}}`: RHSの下限範囲値が返される長さ`nrows`の倍精度配列。
  * `upper::Union{Nothing,AbstractVector{Float64}}`: RHSの上限範囲値が返される長さ`nrows`の倍精度配列。

C APIの対応する関数[XPRSrhssa](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSrhssa.html)のドキュメントも参照してください。
