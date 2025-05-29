```
XPRSfeaturequery(feature)::status
```

指定された機能が最適化ツールで使用されている現在のライセンスで利用可能かどうかを確認します。

# 引数

  * `feature::Union{Nothing,AbstractString}`: ライセンスで確認する機能の文字列。

# 戻り値

  * `status::Int32`: チェックの戻りステータス、値が1の場合は機能が利用可能であることを示します。

対応する関数のドキュメント [XPRSfeaturequery](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSfeaturequery.html) をC APIで参照してください。
