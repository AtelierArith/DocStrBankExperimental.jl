```
vizcircuit(circuit; w_depth=0.85, w_line=0.75, format=:svg, filename=nothing,
    show_ending_bar=false, starting_texts=nothing, starting_offset=-0.3,
    ending_texts=nothing, ending_offset=0.3)
```

`Yao`量子回路を視覚化します。

### キーワード引数

  * `w_depth` は回路の列の幅です。
  * `w_line` は回路の行の幅です。
  * `format` は `:svg`、 `:png` または `:pdf` です。
  * `filename` は `"*.svg"`、 `"*.png"`、 `"*.pdf"` または何も指定しない（ファイルに保存しない）ことができます。
  * `starting_texts` と `ending_texts` は回路の前後に表示されるテキストです。
  * `starting_offset` と `end_offset` は開始および終了テキストのオフセット（実数値）です。
  * `show_ending_bar` は終了バーを表示するためのブールスイッチです。

### スタイル

ゲートのスタイル（色や線）を変更するには、サブモジュール `CircuitStyles` の定数を修正してください。これらは次のように定義されています：

  * CircuitStyles.unit = Ref(60)                      # 単位のポイント数
  * CircuitStyles.r = Ref(0.2)                        # ノードのサイズ
  * CircuitStyles.lw = Ref(1.0)                       # 線の幅
  * CircuitStyles.textsize = Ref(16.0)                # テキストサイズ
  * CircuitStyles.paramtextsize = Ref(10.0)           # テキストサイズ（長いテキスト）
  * CircuitStyles.fontfamily = Ref("JuliaMono")       # フォントファミリー
  * CircuitStyles.linecolor = Ref("#000000")          # 線の色
  * CircuitStyles.gate_bgcolor = Ref("transparent")   # ゲートの背景色
  * CircuitStyles.textcolor = Ref("#000000")          # テキストの色
