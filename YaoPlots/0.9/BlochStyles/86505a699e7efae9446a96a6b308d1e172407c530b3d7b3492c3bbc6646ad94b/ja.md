```
BlochStyles
```

ブロッホ球描画のデフォルトスタイルを定義するモジュールです。デフォルトスタイルを変更するには、このモジュール内の値を変更できます。例えば：

```julia
using YaoPlots
YaoPlots.BlochStyles.lw[] = 2.0
```

### スタイル変数

#### 一般

  * `lw`: 描画の線の太さ
  * `textsize`: テキストのサイズ
  * `fontfamily`: テキストのフォントファミリー
  * `background_color`: 描画の背景色
  * `color`: 描画の色

#### 球体

  * `ball_size`: ボールのサイズ
  * `dot_size`: ドットのサイズ
  * `eye_point`: 描画の視点

#### 軸

  * `axes_lw`: 軸の線の太さ
  * `axes_colors`: 軸の色
  * `axes_texts`: 軸のテキスト、デフォルトは `["x", "y", "z"]`

#### 状態表示

  * `show_projection_lines`: 投影線を表示するかどうか
  * `show_angle_texts`: 角度テキストを表示するかどうか
  * `show_line`: 線を表示するかどうか
  * `show01`: 0および1の状態を表示するかどうか
