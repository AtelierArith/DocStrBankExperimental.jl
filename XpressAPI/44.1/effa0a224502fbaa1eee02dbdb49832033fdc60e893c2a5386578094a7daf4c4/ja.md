```
XPRSiisnext(prob)::status
```

さらなる不可約非実現集合 (IIS) の検索を続けるか、まだIISが特定されていない場合はXPRSiisfirst (IIS) を呼び出します。

# 引数

  * `prob::XPRSprob`: 現在の問題。

# 戻り値

  * `status::Int32`: 検索後のステータス: 0成功; 1これ以上のIISは見つからなかった、またはXPRSiisfirstの呼び出しが前にない場合は問題が実現可能; 2エラー (関数が非ゼロを返す場合)。

C APIの対応する関数[XPRSiisnext](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSiisnext.html)のドキュメントも参照してください。
