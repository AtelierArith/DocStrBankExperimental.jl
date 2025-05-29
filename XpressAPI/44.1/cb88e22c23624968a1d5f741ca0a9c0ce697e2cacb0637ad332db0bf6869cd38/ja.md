```
XPRSslpsetdetrow(prob, nvars, colind, rowind)::prob
```

変数の決定行を設定します

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `nvars::Integer`: 決定行が設定される変数の数。
  * `colind::AbstractVector{Integer}`: 決定行が設定される列のインデックスを持つ長さ`nvars`の配列。
  * `rowind::AbstractVector{Integer}`: 決定行のインデックスを持つ長さ`nvars`の配列。

# 戻り値

  * `prob::XPRSprob`: 現在のSLP問題。

C APIの対応する関数[XPRSslpsetdetrow](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpsetdetrow.html)のドキュメントも参照してください。
