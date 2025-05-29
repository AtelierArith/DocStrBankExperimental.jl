```
write_vtk(box, filename; verbose=true, center_at_origin=false)
write_vtk(crystal)
```

ボックスを .vtk ファイルに書き出して、例えば結晶の単位セル境界を視覚化します。`Crystal` が渡された場合、その結晶のボックスが、結晶構造のファイル名と同じで .vtk 拡張子が付いたファイルに書き出されます。

`filename` が渡されない場合は、自動的に ".vtk" 拡張子が追加されます。

# 引数

  * `box::Box`: ブラベース格子
  * `filename::AbstractString`: .vtk ファイル出力のファイル名（絶対パス）
  * `crystal::Crystal`: 結晶構造オブジェクト
  * `center_at_origin::Bool`: true の場合、ボックスを原点にセンタリングします。false の場合、原点はボックスの隅になります。
  * `verbose::Bool`: true の場合、書き込まれたファイルの名前をコンソールに表示します。
