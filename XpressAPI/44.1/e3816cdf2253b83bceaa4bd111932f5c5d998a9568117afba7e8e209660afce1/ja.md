```
XPRSslpgetrowwt(prob, row)::weight
```

行の初期ペナルティエラー重みを取得します

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `row::Integer`: 重みを取得する行のインデックス。

# 戻り値

  * `weight::Float64`: 重みの値を受け取るための倍精度変数のアドレス。

C APIの対応する関数のドキュメントも参照してください [XPRSslpgetrowwt](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpgetrowwt.html)。
