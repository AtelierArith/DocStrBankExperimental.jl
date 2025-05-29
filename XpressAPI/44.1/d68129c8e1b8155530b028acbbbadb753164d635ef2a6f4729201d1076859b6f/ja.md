```
XPRSsetdblcontrol(prob, control, value)::prob
```

指定されたダブル制御パラメータの値を設定します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `control::Integer`: 値を設定する制御パラメータ。
  * `value::Float64`: 制御パラメータに設定する値。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSsetdblcontrol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSsetdblcontrol.html)のドキュメントも参照してください。
