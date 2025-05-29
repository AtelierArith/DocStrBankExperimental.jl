```
XPRSgetdblcontrol(prob, control)::value
```

指定されたダブル制御パラメータの値を取得します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `control::Integer`: 値を返す制御パラメータ。

# 戻り値

  * `value::Float64`: 制御値が返される場所へのポインタ。

C APIの対応する関数のドキュメント[XPRSgetdblcontrol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetdblcontrol.html)も参照してください。
