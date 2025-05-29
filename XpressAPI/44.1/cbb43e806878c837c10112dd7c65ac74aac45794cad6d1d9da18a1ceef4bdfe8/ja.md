```
XPRSslpgetcoefformula(prob, row, col, parsed, maxtypes, type, value)::factor, ntypes, type, value
```

トークンに分割された式として単一の行列係数を取得します。

この関数の簡易版については、XSLPchgformulaを参照してください。

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `row::Integer`: 係数の行インデックスを保持する整数。
  * `col::Integer`: 係数の列インデックスを保持する整数。
  * `parsed::Integer`: アイテムの式を内部の未解析形式（`parsed`=0）または解析済み（逆ポーランド）形式（`parsed`=1）で返すかどうかを示す整数。
  * `maxtypes::Integer`: 返すトークンの最大数、すなわち`type`および`value`配列の長さ。
  * `type::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: 式のトークンタイプを保持する整数配列。この引数に`XPRS_ALLOC`を渡すことで、関数が適切なサイズの配列を自動的に割り当てます。この引数に`nothing`を渡すことで、その情報を照会しないこともできます。
  * `value::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: `type`に対応する値のダブル配列。この引数に`XPRS_ALLOC`を渡すことで、関数が適切なサイズの配列を自動的に割り当てます。この引数に`nothing`を渡すことで、その情報を照会しないこともできます。

# 戻り値

  * `factor::Float64`: 係数内の式を掛ける定数因子の値を受け取るダブル精度変数のアドレス。
  * `ntypes::Int32`: `type`および`value`で返されたトークンの数。
  * `type::Union{Nothing,AbstractVector{Int32}}`: 式のトークンタイプを保持する整数配列。
  * `value::Union{Nothing,AbstractVector{Float64}}`: `type`に対応する値のダブル配列。

C APIの対応する関数[XPRSslpgetcoefformula](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpgetcoefformula.html)のドキュメントも参照してください。
