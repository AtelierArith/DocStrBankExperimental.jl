```
XPRSgetstrcontrol(prob, control)::value
```

指定された文字列制御パラメータの値を返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `control::Integer`: 値を返す制御パラメータ。

# 戻り値

  * `value::AbstractString`: 制御の値（およびヌル終端子）が返される文字列へのポインタ。

C APIの対応する関数[XPRSgetstrcontrol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetstrcontrol.html)のドキュメントも参照してください。
