```
XPRScalcobjn(prob, objidx, solution)::objval
```

与えられた目的関数の目的値を多目的問題で計算します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `objidx::Integer`: 計算する目的関数のインデックス。
  * `solution::AbstractVector{Number}`: 解を保持する長さ `COLS` のダブル配列、または現在の解を使用するための `nothing`。

# 戻り値

  * `objval::Float64`: 計算された目的値が返されるダブルへのポインタ。

C APIの対応する関数のドキュメント [XPRScalcobjn](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRScalcobjn.html) も参照してください。
