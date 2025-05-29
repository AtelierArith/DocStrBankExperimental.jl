```
XPRSgetdirs(prob, indices, prios, branchdirs, uppseudo, downpseudo)::ndir, indices, prios, branchdirs, uppseudo, downpseudo
```

マトリックスにロードされた指示を返すために使用されます。

優先順位、強制分岐方向、および擬似コストを返すことができます。前処理の後に呼び出された場合、`XPRSgetdirs`は前処理された問題の指示を取得します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `indices::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: 列番号（`0`、`1`、`2`、...）または特別に順序付けられたセットに対応する負の値を含む長さ`ndir`の整数配列。適切なサイズの配列を関数に割り当てさせるために、この引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。
  * `prios::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: 列およびセットの優先順位を含む長さ`ndir`の整数配列で、最小の優先順位を持つ列/セットが最初に分岐されます。適切なサイズの配列を関数に割り当てさせるために、この引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。
  * `branchdirs::Union{XPRSallocatable,Nothing,AbstractVector{Cchar}}`: 各列またはセットの分岐方向を指定する長さ`ndir`の文字配列：Uエンティティは上に強制される; Dエンティティは下に強制される; N指定されていない。適切なサイズの配列を関数に割り当てさせるために、この引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。
  * `uppseudo::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: 列およびセットの上擬似コストを含む長さ`ndir`の倍精度配列。適切なサイズの配列を関数に割り当てさせるために、この引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。
  * `downpseudo::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: 列およびセットの下擬似コストを含む長さ`ndir`の倍精度配列。適切なサイズの配列を関数に割り当てさせるために、この引数に`XPRS_ALLOC`を渡すことができます。この引数に`nothing`を渡すと、その情報を照会しません。

# 戻り値

  * `ndir::Int32`: 指示の数が返される整数へのポインタ。
  * `indices::Union{Nothing,AbstractVector{Int32}}`: 列番号（`0`、`1`、`2`、...）または特別に順序付けられたセットに対応する負の値を含む長さ`ndir`の整数配列。
  * `prios::Union{Nothing,AbstractVector{Int32}}`: 列およびセットの優先順位を含む長さ`ndir`の整数配列で、最小の優先順位を持つ列/セットが最初に分岐されます。
  * `branchdirs::Union{Nothing,AbstractVector{Cchar}}`: 各列またはセットの分岐方向を指定する長さ`ndir`の文字配列：Uエンティティは上に強制される; Dエンティティは下に強制される; N指定されていない。
  * `uppseudo::Union{Nothing,AbstractVector{Float64}}`: 列およびセットの上擬似コストを含む長さ`ndir`の倍精度配列。
  * `downpseudo::Union{Nothing,AbstractVector{Float64}}`: 列およびセットの下擬似コストを含む長さ`ndir`の倍精度配列。

C APIの対応する関数のドキュメント[XPRSgetdirs](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetdirs.html)も参照してください。
