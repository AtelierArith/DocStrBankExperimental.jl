```
write_bond_information(crystal)
write_bond_information(crystal, filename)
write_bond_information(crystal, center_at_origin=false)
write_bond_information(xtal, filename, :cross_boundary => p -> p, "bonds.vtk") # cross-boundary bonds only
write_bond_information(xtal, filename, :distance => d -> d < 1.0, "bonds.vtk") # distance less than 1.0
```

結晶から選択したファイル名にボンド情報を書き込みます。

# 引数

  * `crystal::Crystal`: VTKファイルにボンドを書き込む結晶
  * `filename::AbstractString`: ボンド情報が保存されるファイル名。省略した場合、結晶名がデフォルトになります。
  * `center_at_origin::Bool`: （オプション）座標を結晶の原点に中心を合わせる
  * `bond_filter::Pair{Symbol, Function}`: （オプション）エッジ属性と述語関数のキー-バリューペア。述語がfalseを返す属性を持つボンドは書き込みから除外されます。
  * `verbose::Bool`: （オプション）trueの場合、出力ファイル名をコンソールに表示します。
