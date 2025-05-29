```
instruct!([nlevel=Val(2), ]state, operator, locs[, control_locs, control_configs, theta])
```

量子状態にオペレーターを適用するための統一インターフェースです。`state`を直接変更します。

### 引数

  * `nlevel`は各クディットのレベル数です。
  * `state`は量子状態を表すベクトルまたは行列で、最初の次元はアクティブなキュービット次元、2番目はバッチ次元です。
  * `operator`は量子オペレーターで、`Val(GATE_SYMBOL)`または行列であることができます。
  * `locs::Tuple`は、このゲートが適用される位置を指定するためのタプルです。
  * `control_locs::Tuple`と`control_configs`は、制御位置と制御値を指定するためのタプルです。
  * `theta::Real`はゲートのパラメータで、例えば`Val(:Rx)`ゲートはそのパラメータの実数を取ります。
