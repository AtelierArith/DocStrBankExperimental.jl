```
XPRSgetrowtype(prob, rowtype, first, last)::rowtype
```

指定された範囲内の行の行タイプを返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `rowtype::Union{XPRSallocatable,AbstractVector{Cchar}}`: 行タイプが返される文字配列で、長さは `last-first+1` です。Nは自由制約を示し、Lは `<=` 制約を示し、Eは = 制約を示し、Gは `>=` 制約を示し、Rは範囲制約を示します。この引数に `XPRS_ALLOC` を渡すことで、関数が適切なサイズの配列を自動的に割り当てます。
  * `first::Integer`: 範囲内の最初の行。
  * `last::Integer`: 範囲内の最後の行。

# 戻り値

  * `rowtype::AbstractVector{Cchar}`: 行タイプが返される文字配列で、長さは `last-first+1` です。Nは自由制約を示し、Lは `<=` 制約を示し、Eは = 制約を示し、Gは `>=` 制約を示し、Rは範囲制約を示します。

C APIの対応する関数 [XPRSgetrowtype](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetrowtype.html) のドキュメントも参照してください。
