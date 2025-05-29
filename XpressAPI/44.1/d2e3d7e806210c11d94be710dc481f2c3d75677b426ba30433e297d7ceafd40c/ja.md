```
XPRSsetstrcontrol(prob, control, value)::prob
```

指定された文字列制御パラメータの値を設定するために使用されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `control::Integer`: 値を設定する制御パラメータ。
  * `value::Union{Nothing,AbstractString}`: 制御を設定する値を含む文字列（およびヌル終端子）。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSsetstrcontrol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSsetstrcontrol.html)のドキュメントも参照してください。
