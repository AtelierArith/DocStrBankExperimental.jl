```
XPRSgetgencons(prob, contype, resultant, colstart, colind, maxcols, valstart, val, maxvals, first, last)::contype, resultant, colstart, colind, ncols, valstart, val, nvals
```

指定された範囲内の一般制約 `y = f(x1, ..., xn, c1, ..., cm)` を返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `contype::Union{XPRSallocatable,Nothing,AbstractVector{XPRSGenConsType}}`: 必要ない場合は `nothing`、または長さが少なくとも `last-first+1` の整数配列で、一般制約のタイプが格納されます: XPRS*GENCONS*MAX (0)は `最大` 制約を示します; XPRS*GENCONS*MIN (1)は `最小` 制約を示します; XPRS*GENCONS*AND (2)は `and` 制約を示します。この引数に `XPRS_ALLOC` を渡すと、関数が適切なサイズの配列を自動的に割り当てます。この引数に `nothing` を渡すと、その情報を照会しません。
  * `resultant::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: 出力変数 `y` のインデックスが格納される整数配列です。この引数に `XPRS_ALLOC` を渡すと、関数が適切なサイズの配列を自動的に割り当てます。この引数に `nothing` を渡すと、その情報を照会しません。
  * `colstart::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: 長さが少なくとも `last-first+2` の整数配列で、`colind` 配列内の各一般制約の開始インデックスが格納されます。この引数に `XPRS_ALLOC` を渡すと、関数が適切なサイズの配列を自動的に割り当てます。この引数に `nothing` を渡すと、その情報を照会しません。
  * `colind::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: 入力変数 `xi` のインデックスが格納される整数配列です。この引数に `XPRS_ALLOC` を渡すと、関数が適切なサイズの配列を自動的に割り当てます。この引数に `nothing` を渡すと、その情報を照会しません。
  * `maxcols::Integer`: 取得する入力列の最大数。
  * `valstart::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: 長さが少なくとも `last-first+2` の整数配列で、`val` 配列内の各一般制約の開始インデックスが格納されます。この引数に `XPRS_ALLOC` を渡すと、関数が適切なサイズの配列を自動的に割り当てます。この引数に `nothing` を渡すと、その情報を照会しません。
  * `val::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: 定数値 `ci` が格納される整数配列です。この引数に `XPRS_ALLOC` を渡すと、関数が適切なサイズの配列を自動的に割り当てます。この引数に `nothing` を渡すと、その情報を照会しません。
  * `maxvals::Integer`: 取得する定数値の最大数。
  * `first::Integer`: 範囲内の最初の一般制約。
  * `last::Integer`: 範囲内の最後の一般制約。

# 戻り値

  * `contype::Union{Nothing,AbstractVector{XPRSGenConsType}}`: 必要ない場合は `nothing`、または長さが少なくとも `last-first+1` の整数配列で、一般制約のタイプが格納されます: XPRS*GENCONS*MAX (0)は `最大` 制約を示します; XPRS*GENCONS*MIN (1)は `最小` 制約を示します; XPRS*GENCONS*AND (2)は `and` 制約を示します。
  * `resultant::Union{Nothing,AbstractVector{Int32}}`: 出力変数 `y` のインデックスが格納される整数配列です。
  * `colstart::Union{Nothing,AbstractVector{Int32}}`: 長さが少なくとも `last-first+2` の整数配列で、`colind` 配列内の各一般制約の開始インデックスが格納されます。
  * `colind::Union{Nothing,AbstractVector{Int32}}`: 入力変数 `xi` のインデックスが格納される整数配列です。
  * `ncols::Int32`: `colind` 配列内の入力列の数を返すポインタ。
  * `valstart::Union{Nothing,AbstractVector{Int32}}`: 長さが少なくとも `last-first+2` の整数配列で、`val` 配列内の各一般制約の開始インデックスが格納されます。
  * `val::Union{Nothing,AbstractVector{Float64}}`: 定数値 `ci` が格納される整数配列です。
  * `nvals::Int32`: `val` 配列内の定数値の数を返すポインタ。

対応する関数のドキュメント [XPRSgetgencons](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetgencons.html) も参照してください。
