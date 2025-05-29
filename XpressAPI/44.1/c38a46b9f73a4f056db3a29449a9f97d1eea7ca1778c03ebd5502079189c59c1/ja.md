```
XPRScalcslacks(prob, solution, slacks)::slacks
```

与えられた解に対する行スラック値を計算します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `solution::AbstractVector{Number}`: スラックを計算するための解を保持する長さCOLSのダブル配列。
  * `slacks::Union{XPRSallocatable,AbstractVector{Float64}}`: 計算された行スラックが返される長さROWSのダブル配列。この引数に`XPRS_ALLOC`を渡すことで、関数が適切なサイズの配列を自動的に割り当てます。

# 戻り値

  * `slacks::AbstractVector{Float64}`: 計算された行スラックが返される長さROWSのダブル配列。

C APIの対応する関数のドキュメントも参照してください [XPRScalcslacks](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRScalcslacks.html)。
