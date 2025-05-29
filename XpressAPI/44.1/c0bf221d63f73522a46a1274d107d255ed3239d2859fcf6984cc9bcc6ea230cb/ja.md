```
XPRScalcsolinfo(prob, solution, duals, property)::value
```

与えられたプライマルおよびデュアルソリューションの最大不適合性のような、ソリューションの必要なプロパティを計算します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `solution::AbstractVector{Number}`: ソリューションを保持する長さCOLSのダブル配列。
  * `duals::AbstractVector{Number}`: デュアルソリューションを保持する長さROWSのダブル配列。
  * `property::Integer`: 計算されるプロパティを定義します。

# 戻り値

  * `value::Float64`: 計算された値が返されるダブルへのポインタ。

C APIの対応する関数[XPRScalcsolinfo](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRScalcsolinfo.html)のドキュメントも参照してください。
