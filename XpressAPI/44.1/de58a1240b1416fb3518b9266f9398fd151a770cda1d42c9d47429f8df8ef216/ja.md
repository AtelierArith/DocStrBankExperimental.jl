```
XPRSgetnlpsol(prob, x, slack, duals, djs)::x, slack, duals, djs
```

**非推奨**XPRSgetsolutionおよび関連する関数を代わりに使用してください。

現在のSLP解の値を取得します。

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `x::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: プライマル変数の値を保持するための長さ`XSLP_ORIGINALCOLS`の倍精度配列。適切なサイズの配列を関数に割り当てさせるために、この引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。
  * `slack::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: スラック変数の値を保持するための長さ`XSLP_ORIGINALROWS`の倍精度配列。適切なサイズの配列を関数に割り当てさせるために、この引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。
  * `duals::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: 双対変数の値を保持するための長さ`XSLP_ORIGINALROWS`の倍精度配列。適切なサイズの配列を関数に割り当てさせるために、この引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。
  * `djs::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: プライマル変数の縮小コストを保持するための長さ`XSLP_ORIGINALCOLS`の倍精度配列。適切なサイズの配列を関数に割り当てさせるために、この引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。

# 戻り値

  * `x::Union{Nothing,AbstractVector{Float64}}`: プライマル変数の値を保持するための長さ`XSLP_ORIGINALCOLS`の倍精度配列。
  * `slack::Union{Nothing,AbstractVector{Float64}}`: スラック変数の値を保持するための長さ`XSLP_ORIGINALROWS`の倍精度配列。
  * `duals::Union{Nothing,AbstractVector{Float64}}`: 双対変数の値を保持するための長さ`XSLP_ORIGINALROWS`の倍精度配列。
  * `djs::Union{Nothing,AbstractVector{Float64}}`: プライマル変数の縮小コストを保持するための長さ`XSLP_ORIGINALCOLS`の倍精度配列。

C APIの対応する関数[XPRSgetnlpsol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetnlpsol.html)のドキュメントも参照してください。
