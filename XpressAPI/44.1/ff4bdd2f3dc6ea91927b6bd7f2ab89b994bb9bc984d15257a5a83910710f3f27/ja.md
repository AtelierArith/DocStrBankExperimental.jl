```
XPRSgetcutslack(prob, cutind)::slack
```

現在のLP緩和解に対するカットのスラック値を計算するために使用されます。

スラックはカット自体から計算され、問題に現在ロードされていないカットについても要求することができます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `cutind::Ptr{Cvoid}`: スラックを計算するカットのポインタ。

# 戻り値

  * `slack::Float64`: スラックの値が返されるダブルポインタ。

C APIの対応する関数[XPRSgetcutslack](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcutslack.html)のドキュメントも参照してください。
