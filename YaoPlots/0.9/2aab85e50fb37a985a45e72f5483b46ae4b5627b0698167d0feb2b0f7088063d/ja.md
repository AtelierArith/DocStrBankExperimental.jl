```julia
bloch_sphere(
    states...;
    textsize,
    color,
    drawing_size,
    offset_x,
    offset_y,
    filename,
    format,
    fontfamily,
    background_color,
    lw,
    eye_point,
    extra_kwargs...
) -> Luxor.Drawing

```

ブロッホ球を描画します。入力は `string => state` ペアのリストで、文字列は状態のラベルであり、状態はサイズ2の複素ベクトル、Yaoレジスタ、または `DensityMatrix` であることができます。生の描画を取得したい場合は、代わりに `draw_bloch_sphere` を使用してください。

### キーワード引数

注意: デフォルト値はサブモジュール `BlochStyles` で指定できます。

  * `textsize`: テキストのサイズ
  * `color`: 描画の色
  * `drawing_size`: 描画のサイズ
  * `offset_x`: x方向の描画のオフセット
  * `offset_y`: y方向の描画のオフセット
  * `filename`: 出力ファイルのファイル名。指定されていない場合、一時ファイルが使用されます
  * `format`: 出力ファイルの形式。指定されていない場合、ファイル名から形式が推測されます
  * `fontfamily`: テキストのフォントファミリー
  * `background_color`: 描画の背景色
  * `lw`: 描画の線の幅
  * `eye_point`: 描画の視点
  * `extra_kwargs`: `draw_bloch_sphere` に渡される追加のキーワード引数

      * `dot_size`: ドットのサイズ
      * `ball_size`: ボールのサイズ
      * `show_projection_lines`: 投影線を表示するかどうか
      * `show_angle_texts`: 角度テキストを表示するかどうか
      * `show_line`: 線を表示するかどうか
      * `show01`: 0および1の状態を表示するかどうか
      * `colors`: 状態の色
      * `axes_lw`: 軸の線の幅
      * `axes_textsize`: 軸のテキストのサイズ
      * `axes_colors`: 軸の色
      * `axes_texts`: 軸のテキスト

### 例

```jldoctest
julia> using YaoPlots, YaoArrayRegister

julia> bloch_sphere("|ψ⟩"=>rand_state(1), "ρ"=>density_matrix(rand_state(2), 1));
```
