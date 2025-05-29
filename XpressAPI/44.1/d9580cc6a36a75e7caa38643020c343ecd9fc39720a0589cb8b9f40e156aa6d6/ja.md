```
XPRSloadlp64(prob, probname, ncols, nrows, rowtype, rhs, rng, objcoef, start, collen, rowind, rowcoef, lb, ub)::prob
```

ユーザーがファイルから行列を読み込むのではなく、行列を直接オプティマイザに渡すことを可能にします。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `probname::Union{Nothing,AbstractString}`: 問題の名前を含む最大 MAXPROBNAMELENGTH 文字の文字列。
  * `ncols::Integer`: 行列の構造的な列の数。
  * `nrows::Integer`: 行列の行の数（目的関数を含まない）。
  * `rowtype::AbstractVector{Cchar}`: 行のタイプを含む長さ `nrows` の文字配列: L は `<=` 制約を示し; E は = 制約を示し; G は `>=` 制約を示し; R は範囲制約を示し; N は非拘束制約を示します。
  * `rhs::AbstractVector{Number}`: 行の右辺係数を含む長さ `nrows` の倍精度配列。
  * `rng::AbstractVector{Number}`: 範囲行の範囲値を含む長さ `nrows` の倍精度配列。
  * `objcoef::AbstractVector{Number}`: 目的関数の係数を含む長さ `ncols` の倍精度配列。
  * `start::AbstractVector{Integer}`: 各列の要素の開始位置の `rowind` および `rowcoef` 配列内のオフセットを含む整数配列。
  * `collen::AbstractVector{Integer}`: 各列の非ゼロ要素の数を含む長さ `ncols` の整数配列。
  * `rowind::AbstractVector{Integer}`: 各列の非ゼロ要素の行インデックスを含む整数配列。
  * `rowcoef::AbstractVector{Number}`: 非ゼロ要素の値を含む倍精度配列; `rowind` と同じ長さ。
  * `lb::AbstractVector{Number}`: 列の下限を含む長さ `ncols` の倍精度配列。
  * `ub::AbstractVector{Number}`: 列の上限を含む長さ `ncols` の倍精度配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C API の対応する関数 [XPRSloadlp64](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSloadlp64.html) のドキュメントも参照してください。
