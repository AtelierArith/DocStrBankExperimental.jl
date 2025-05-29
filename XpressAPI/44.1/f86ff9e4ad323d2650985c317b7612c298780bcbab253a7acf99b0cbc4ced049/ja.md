```
XPRSchgrowtype(prob, nrows, rowind, rowtype)::prob
```

行のタイプを行列内で変更するために使用されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `nrows::Integer`: 変更する行の数。
  * `rowind::AbstractVector{Integer}`: 行のインデックスを含む長さ `nrows` の整数配列。
  * `rowtype::AbstractVector{Cchar}`: 新しい行タイプを与える長さ `nrows` の文字配列: Lは `<=` 行を示し; Eは = 行を示し; Gは `>=` 行を示し; Rは範囲行を示し; Nは自由行を示します。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数 [XPRSchgrowtype](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSchgrowtype.html) のドキュメントも参照してください。
