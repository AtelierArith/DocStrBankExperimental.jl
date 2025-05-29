```
XPRS_bo_validate(bo)::status
```

与えられた分岐オブジェクトがMIP解の現在の分岐および境界ノードで分岐するのに有効であることを検証します。

この関数は、すべての分岐が空でないことを確認し、必要に応じて分岐オブジェクトが事前解決できるかどうかを検証します。

# 引数

  * `bo::XPRSbranchobject`: 分岐オブジェクト。

# 戻り値

  * `status::Int32`: 提供された分岐オブジェクトのチェックから返されるステータス: 0オブジェクトは受け入れ可能です。

対応する関数のドキュメント [XPRS*bo*validate](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRS_bo_validate.html) をC APIで参照してください。
