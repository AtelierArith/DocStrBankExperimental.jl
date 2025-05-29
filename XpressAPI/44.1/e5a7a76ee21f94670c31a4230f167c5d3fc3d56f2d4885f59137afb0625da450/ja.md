```
XPRSgetobj(prob, objcoef, first, last)::objcoef
```

指定された範囲内の列に対する目的関数の係数を返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `objcoef::Union{XPRSallocatable,AbstractVector{Float64}}`: 目的関数の係数を配置するための長さ `last-first+1` のダブル配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。
  * `first::Integer`: 範囲内の最初の列。
  * `last::Integer`: 範囲内の最後の列。

# 戻り値

  * `objcoef::AbstractVector{Float64}`: 目的関数の係数を配置するための長さ `last-first+1` のダブル配列。

C APIの対応する関数 [XPRSgetobj](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetobj.html) のドキュメントも参照してください。
