```
XPRSgetlastbarsol(prob, x, slack, duals, djs)::x, slack, duals, djs, status
```

最適化にバリアソルバーを使用した後の最後のバリア解の値を取得するために使用されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `x::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: プライマル変数の値が返される長さORIGINALCOLSのダブル配列。適切なサイズの配列を関数が割り当てるようにするには、この引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。
  * `slack::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: スラック変数の値が返される長さORIGINALROWSのダブル配列。適切なサイズの配列を関数が割り当てるようにするには、この引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。
  * `duals::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: 双対変数の値が返される長さ`ORIGINALROWS`のダブル配列（cBTB-1）。適切なサイズの配列を関数が割り当てるようにするには、この引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。
  * `djs::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: 各変数の縮小コストが返される長さ`ORIGINALCOLS`のダブル配列（cT-cBTB-1A）。適切なサイズの配列を関数が割り当てるようにするには、この引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。

# 戻り値

  * `x::Union{Nothing,AbstractVector{Float64}}`: プライマル変数の値が返される長さORIGINALCOLSのダブル配列。
  * `slack::Union{Nothing,AbstractVector{Float64}}`: スラック変数の値が返される長さORIGINALROWSのダブル配列。
  * `duals::Union{Nothing,AbstractVector{Float64}}`: 双対変数の値が返される長さ`ORIGINALROWS`のダブル配列（cBTB-1）。
  * `djs::Union{Nothing,AbstractVector{Float64}}`: 各変数の縮小コストが返される長さ`ORIGINALCOLS`のダブル配列（cT-cBTB-1A）。
  * `status::Int32`: 最後のバリア解のステータス。

C APIの対応する関数[XPRSgetlastbarsol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetlastbarsol.html)のドキュメントも参照してください。
