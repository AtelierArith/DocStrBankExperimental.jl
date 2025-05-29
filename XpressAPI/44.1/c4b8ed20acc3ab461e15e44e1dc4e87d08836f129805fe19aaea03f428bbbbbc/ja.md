```
XPRSbasisstability(prob, type, norm, scaled)::value
```

現在の基準の安定性に関するさまざまな指標を計算し、基準条件数を含みます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `type::Integer`: 0基準の条件数。
  * `norm::Integer`: 0無限大ノルムを使用します。
  * `scaled::Integer`: 安定性値をスケーリングされた行列または非スケーリング行列で計算するかどうか。

# 戻り値

  * `value::Float64`: 計算された値が返されるダブルへのポインタ。

C APIの対応する関数[XPRSbasisstability](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSbasisstability.html)のドキュメントも参照してください。
