```
XPRSaddgencons(prob, ncons, ncols, nvals, contype, resultant, colstart, colind, valstart, val)::prob
```

問題に1つ以上の一般制約を追加します。

各一般制約 `y = f(x1, ..., xn, c1, ..., cn)` は、1つ以上の（入力）列 xi、0個以上の定数値 ci、およびすべての xi とは異なる結果（出力列）y で構成されます。一般制約には `maximum` と `minimum`（任意の型の入力列の任意の数と、少なくとも1つの合計の入力値）、`and` と `or`（少なくとも1つのバイナリ入力列、定数値なし、バイナリ結果）、および `absolute value`（任意の型の入力列が正確に1つ、定数値なし）が含まれます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `ncons::Integer`: 追加する一般制約の数。
  * `ncols::Integer`: 追加する一般制約における入力変数の合計数。
  * `nvals::Integer`: 追加する一般制約における定数値の合計数。
  * `contype::AbstractVector{XPRSGenConsType}`: 一般制約のタイプを含む長さ `ncons` の整数配列：XPRS*GENCONS*MAX (0)は `maximum` 制約を示し、XPRS*GENCONS*MIN (1)は `minimum` 制約を示し、XPRS*GENCONS*AND (2)は `and` 制約を示します。
  * `resultant::AbstractVector{Integer}`: 一般制約の出力変数のインデックスを含む長さ `ncons` の整数配列。
  * `colstart::AbstractVector{Integer}`: `colind` 配列における各一般制約の開始インデックスを含む長さ `ncons` の整数配列。
  * `colind::AbstractVector{Integer}`: すべての一般制約における入力変数を含む長さ `ncols` の整数配列。
  * `valstart::AbstractVector{Integer}`: `val` 配列における各一般制約の開始インデックスを含む長さ `ncons` の整数配列（`ncoefs = 0` の場合は `nothing` である可能性があります）。
  * `val::AbstractVector{Number}`: すべての一般制約における定数値を含む長さ `nvals` の倍精度配列（`ncoefs = 0` の場合は `nothing` である可能性があります）。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C API の対応する関数 [XPRSaddgencons](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSaddgencons.html) のドキュメントも参照してください。
