```
XPRSslpgetccoef(prob, row, col, maxbytes)::factor, formula
```

**非推奨**XPRSslpgetcoefstrの代わりに使用してください。

文字列内の数式として単一の行列係数を取得します。この関数の簡易版については、XPRSnlpgetformulastrを参照してください。

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `row::Integer`: 係数の行インデックスを保持する整数。
  * `col::Integer`: 係数の列インデックスを保持する整数。
  * `maxbytes::Integer`: 返される数式の最大長。

# 戻り値

  * `factor::Float64`: 係数内の数式を掛ける定数因子の値を受け取るための倍精度変数のアドレス。
  * `formula::AbstractString`: ファイルからの入力に使用されるのと同じ形式で数式が配置される文字バッファ。

C APIの対応する関数[XPRSslpgetccoef](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpgetccoef.html)のドキュメントも参照してください。
