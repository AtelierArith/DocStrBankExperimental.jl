```
XPRSiisstatus(prob, nrows, ncols, suminfeas, numinfeas)::niis, nrows, ncols, suminfeas, numinfeas
```

XPRSiisfirst (IIS)、XPRSiisnext (IIS `-n`) または XPRSiisall (IIS `-a`) によってこれまでに見つかった不可約非可行集合 (IIS) に関する統計を返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `nrows::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: IIS の行数。適切なサイズの配列を関数が割り当てるようにするには、この引数に `XPRS_ALLOC` を渡すことができます。この引数に `nothing` を渡すと、その情報を照会しません。
  * `ncols::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: IIS の境界の数。この引数に `XPRS_ALLOC` を渡すと、関数が適切なサイズの配列を割り当てるようにします。この引数に `nothing` を渡すと、その情報を照会しません。
  * `suminfeas::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: 最初のフェーズの単体法後の IIS における非可行性の合計。この引数に `XPRS_ALLOC` を渡すと、関数が適切なサイズの配列を割り当てるようにします。この引数に `nothing` を渡すと、その情報を照会しません。
  * `numinfeas::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: 最初のフェーズの単体法後の IIS における非可行変数の数。この引数に `XPRS_ALLOC` を渡すと、関数が適切なサイズの配列を割り当てるようにします。この引数に `nothing` を渡すと、その情報を照会しません。

# 戻り値

  * `niis::Int32`: これまでに見つかった IIS の数。
  * `nrows::Union{Nothing,AbstractVector{Int32}}`: IIS の行数。
  * `ncols::Union{Nothing,AbstractVector{Int32}}`: IIS の境界の数。
  * `suminfeas::Union{Nothing,AbstractVector{Float64}}`: 最初のフェーズの単体法後の IIS における非可行性の合計。
  * `numinfeas::Union{Nothing,AbstractVector{Int32}}`: 最初のフェーズの単体法後の IIS における非可行変数の数。

C API の対応する関数 [XPRSiisstatus](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSiisstatus.html) のドキュメントも参照してください。
