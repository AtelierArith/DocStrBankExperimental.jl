```
XPRSnlpsetinitval(prob, nvars, colind, initial)::prob
```

変数の初期値を設定します

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `nvars::Integer`: 初期値を設定する変数の数。
  * `colind::AbstractVector{Integer}`: 初期値が提供される列のインデックスを持つ長さ`nvars`の配列。
  * `initial::AbstractVector{Number}`: 初期値を持つ長さ`nvars`の配列。

# 戻り値

  * `prob::XPRSprob`: 現在のSLP問題。

C APIの対応する関数[XPRSnlpsetinitval](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlpsetinitval.html)のドキュメントも参照してください。
