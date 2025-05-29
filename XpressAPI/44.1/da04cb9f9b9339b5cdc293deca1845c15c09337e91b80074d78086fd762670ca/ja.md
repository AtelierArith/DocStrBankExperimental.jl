```
XPRStunerwritemethod(prob, methodfile)::prob
```

この関数は、現在のチューナーメソッドを指定されたファイルに書き込むか、コンソールに出力します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `methodfile::Union{Nothing,AbstractString}`: チューナーが現在のチューナーメソッドを書き込むメソッドファイル名。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

関連する関数のドキュメントも参照してください [XPRStunerwritemethod](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRStunerwritemethod.html) C API の。
