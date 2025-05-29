```
XPRSgetindex(prob, type, name)::index
```

指定された行または列名のインデックスを返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `type::Integer`: 行インデックスが必要な場合は`XPRS*NAMES*ROW`(=1)を指定; 列インデックスが必要な場合は`XPRS*NAMES*COLUMN`(=2)を指定; セットインデックスが必要な場合は`XPRS*NAMES*SET`(=3)を指定; ピースワイズ線形制約インデックスが必要な場合は`XPRS*NAMES*PWLCONS`(=4)を指定; 一般制約インデックスが必要な場合は`XPRS*NAMES*GENCONS`(=5)を指定; 目的インデックスが必要な場合は`XPRS*NAMES*OBJECTIVE`(=6)を指定; ユーザ関数インデックスが必要な場合は`XPRS*NAMES*USERFUNC`(=7)を指定; 内部関数インデックスが必要な場合は`XPRS*NAMES*INTERNALFUNC`(=8)を指定。
  * `name::Union{Nothing,AbstractString}`: ヌル終端文字列。

# 戻り値

  * `index::Int32`: 行または列インデックス番号が返される整数のポインタ。

C APIの対応する関数のドキュメントも参照してください [XPRSgetindex](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetindex.html)。
