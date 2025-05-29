```
XPRSgetprobname(prob)::name
```

現在の問題名を返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。

# 戻り値

  * `name::AbstractString`: 現在の問題名を含む最大 MAXPROBNAMELENGTH 文字の文字列。

C API の対応する関数 [XPRSgetprobname](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetprobname.html) のドキュメントも参照してください。
