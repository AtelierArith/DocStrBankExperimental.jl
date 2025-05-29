```
XPRSslpgetrowstatus(prob, row)::status
```

制約のステータス設定を取得します

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `row::Integer`: データを取得する行列の行のインデックス。

# 戻り値

  * `status::Int32`: ステータス設定を受け取るビットマップを保持する整数のアドレス。

C APIの対応する関数[XPRSslpgetrowstatus](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpgetrowstatus.html)のドキュメントも参照してください。
