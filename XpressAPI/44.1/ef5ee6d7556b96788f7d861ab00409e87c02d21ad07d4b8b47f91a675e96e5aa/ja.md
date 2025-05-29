```
XPRSalter(prob, filename)::prob
```

現在の問題の行列要素、右辺、および制約の感覚を変更または変更します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `filename::Union{Nothing,AbstractString}`: 読み込むファイルを指定する最大MAXPROBNAMELENGTH文字の文字列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSalter](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSalter.html)のドキュメントも参照してください。
