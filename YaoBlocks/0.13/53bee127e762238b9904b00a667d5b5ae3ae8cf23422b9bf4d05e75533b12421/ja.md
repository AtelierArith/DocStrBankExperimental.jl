```
TimeEvolution{D, TT, GT} <: PrimitiveBlock{D}
```

TimeEvolution、ここでGTはブロックタイプです。入力行列はエルミートである必要があります。

!!! note
    `TimeEvolution` コンストラクタはデフォルトで入力ブロックのエルミート性をチェックしますが、時には遅くなることがあります。オプションパラメータ `check_hermicity = false` を指定することで、手動でチェックをオフにすることができます。

