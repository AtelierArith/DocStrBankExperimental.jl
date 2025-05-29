```
XPRSgetcallbackredcosts(prob, djs, first, last)::available, djs
```

現在のコールバックに関連付けられた解からの削減コストを返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `djs::Union{XPRSallocatable,AbstractVector{Float64}}`: 変数の削減コストが返される長さ `last-first+1` のダブル配列。適切なサイズの配列を関数に割り当てさせるために、この引数に `XPRS_ALLOC` を渡すことができます。
  * `first::Integer`: 返す削減コストの最初の列。
  * `last::Integer`: 返す削減コストの最後の列。

# 戻り値

  * `available::Int32`: 双対解が利用可能な場合、この変数は1に設定されます。
  * `djs::AbstractVector{Float64}`: 変数の削減コストが返される長さ `last-first+1` のダブル配列。

C APIの対応する関数 [XPRSgetcallbackredcosts](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcallbackredcosts.html) のドキュメントも参照してください。
