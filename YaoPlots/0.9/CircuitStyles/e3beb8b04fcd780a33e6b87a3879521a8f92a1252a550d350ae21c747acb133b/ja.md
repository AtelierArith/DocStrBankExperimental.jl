```
CircuitStyles
```

回路の視覚化のスタイルを定義するモジュールです。スタイルを変更するには、このモジュール内の変数を修正してください。例えば、

```julia
julia> using YaoPlots

julia> YaoPlots.CircuitStyles.unit[] = 40
40
```

### スタイル変数

#### サイズ

  * `unit` は単位のピクセル数です。
  * `r` はノードのサイズです。
  * `lw` は線の幅です。

#### テキスト

  * `textsize` はテキストのサイズです。
  * `paramtextsize` は長いテキストのためのテキストサイズです。
  * `fontfamily` はフォントファミリーです。

#### 色

  * `linecolor` は線の色です。
  * `gate_bgcolor` はゲートの背景色です。
  * `textcolor` はテキストの色です。
