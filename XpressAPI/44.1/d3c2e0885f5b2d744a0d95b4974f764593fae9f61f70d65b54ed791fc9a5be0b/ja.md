```
XPRSgetbasisval(prob, row, col)::rowstat, colstat
```

特定の列または行の現在の基準ステータスを返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `row::Integer`: 行の基準ステータスを取得するための行インデックス。
  * `col::Integer`: 列の基準ステータスを取得するための列インデックス。

# 戻り値

  * `rowstat::Int32`: 行の基準ステータスの値が返される整数ポインタ。
  * `colstat::Int32`: 列の基準ステータスの値が返される整数ポインタ。

C APIの対応する関数[XPRSgetbasisval](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetbasisval.html)のドキュメントも参照してください。
