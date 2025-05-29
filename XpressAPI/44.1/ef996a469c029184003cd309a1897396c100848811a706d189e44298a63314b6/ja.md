```
XPRS_bo_store(bo)::status
```

新しいユーザー分岐オブジェクトをオプティマイザの分岐候補リストに追加します。

この関数は、XPRSaddcboptnodeによって設定されたコールバック関数を通じてのみ利用可能です。

# 引数

  * `bo::XPRSbranchobject`: 保存する新しいユーザー分岐オブジェクト。

# 戻り値

  * `status::Int32`: 提供された分岐オブジェクトのチェックから返されたステータス: 0オブジェクトは正常に受け入れられました。

関連する関数のドキュメント [XPRS*bo*store](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRS_bo_store.html) をC APIで参照してください。
