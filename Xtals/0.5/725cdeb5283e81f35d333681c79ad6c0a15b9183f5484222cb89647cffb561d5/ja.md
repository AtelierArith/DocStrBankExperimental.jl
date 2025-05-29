```
write_xyz(atoms, filename; comment="")
write_xyz(crystal; comment="", center_at_origin=false)
write_xyz(molecules, box, filename; comment="") # fractional
write_xyz(molecules, box, filename; comment="") # Cartesian
```

原子を .xyz ファイルに書き込みます。

# 引数

  * `atoms::Atoms`: 原子のセット。
  * `filename::AbstractString`: .xyz ファイルのファイル名（絶対パス）。（拡張子が提供されていない場合は ".xyz" が自動的に追加されます。）
  * `comment::AbstractString`: ファイルに書き込みたいコメント。
  * `center_at_origin::Bool`: （結晶のみ）`true` の場合、すべての座標を単位セルの中心が原点になるように移動します。
