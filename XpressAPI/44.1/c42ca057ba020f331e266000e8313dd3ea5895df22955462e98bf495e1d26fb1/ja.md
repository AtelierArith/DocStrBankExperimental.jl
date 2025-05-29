```
XPRSloadsecurevecs(prob, nrows, ncols, rowind, colind)::prob
```

ユーザーが行と列をマークして、プレソルブがこれらの行と列を行列から削除するのを防ぐことができます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `nrows::Integer`: マークする行の数。
  * `ncols::Integer`: マークする列の数。
  * `rowind::AbstractVector{Integer}`: マークする行を含む長さ `nrows` の整数配列。
  * `colind::AbstractVector{Integer}`: マークする列を含む長さ `ncols` の整数配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数 [XPRSloadsecurevecs](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSloadsecurevecs.html) のドキュメントも参照してください。
