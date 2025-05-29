```
XPRSgetmipsolval(prob, col, row)::x, slack
```

**非推奨**XPRSgetsolutionおよびXPRSgetslacksを代わりに使用してください。

最後に見つかったMIPソリューションの単一のソリューション値を取得するために使用されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `col::Integer`: ソリューション値を返す変数の列インデックス。
  * `row::Integer`: ソリューション値を返す制約の行インデックス。

# 戻り値

  * `x::Float64`: プライマル変数の値が返されるダブルポインタ。
  * `slack::Float64`: スラック変数の値が返されるダブルポインタ。

C APIの対応する関数[XPRSgetmipsolval](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetmipsolval.html)のドキュメントも参照してください。
