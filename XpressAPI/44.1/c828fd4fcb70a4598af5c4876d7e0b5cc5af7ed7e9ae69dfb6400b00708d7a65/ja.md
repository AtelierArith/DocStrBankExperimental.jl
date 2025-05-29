```
XPRSaddobj(prob, ncols, colind, objcoef, priority, weight)::prob
```

与えられた係数を持つ目的関数を多目的問題に追加します。

目的の重みと優先度は、指定された値に設定されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `ncols::Integer`: 追加する目的関数係数要素の数。
  * `colind::AbstractVector{Integer}`: 目的係数が変更される列のインデックスを含む長さ `ncols` の整数配列。
  * `objcoef::AbstractVector{Number}`: 新しい目的関数係数を与える長さ `ncols` の倍精度配列。
  * `priority::Integer`: 目的関数の優先度。
  * `weight::Float64`: 目的関数の重み。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数 [XPRSaddobj](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSaddobj.html) のドキュメントも参照してください。
