```
XPRSslpchgcascadenlimit(prob, col, limit)::prob
```

特定のカスケード反復制限を設定します

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `col::Integer`: カスケード制限を課すSLP変数に対応する列のインデックス。
  * `limit::Integer`: 新しいカスケード反復制限。

# 戻り値

  * `prob::XPRSprob`: 現在のSLP問題。

対応する関数のドキュメントも参照してください [XPRSslpchgcascadenlimit](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpchgcascadenlimit.html) C APIで。
