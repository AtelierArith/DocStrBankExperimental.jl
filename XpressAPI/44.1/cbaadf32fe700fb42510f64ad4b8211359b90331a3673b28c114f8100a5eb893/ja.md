```
XPRS_OPTIMALITYTOL
```

単純形法: これは削減コストに対するゼロの許容誤差です。(double)

各イテレーションで、単純形法は負の削減コストを持つ基底に入る変数を探します。候補は、`OPTIMALITYTOL`の負の値よりも削減コストが小さい変数のみです。

デフォルト値: `1.0E-06`

ドメイン: (0,+INF]
