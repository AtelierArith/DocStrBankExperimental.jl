```
`view_crystal(xtal, drop_cross_pb_bonds=true)`
```

クリスタルを表示するGUIウィンドウを起動します。

# 引数

  * `xtal::Crystal` : 表示するクリスタル
  * `drop_cross_pb_bonds::Bool` : オプション。単位セルの周期境界を越えて延びる結合を削除するには`true`に設定します（これらは視覚化を乱す傾向があります）。デフォルトは`true`です。
