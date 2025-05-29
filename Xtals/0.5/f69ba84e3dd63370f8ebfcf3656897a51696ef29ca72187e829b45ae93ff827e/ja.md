```
write_cif(crystal, filename; fractional_coords=true, number_atoms=true)
write_cif(crystal) # writes to file crystal.name[.cif]
```

`crystal::Crystal`を.cifファイルに書き込みます。

# 引数

  * `crystal::Crystal`: ファイルに書き込む結晶
  * `filename::AbstractString`: `.cif`ファイルのファイル名。拡張子に".cif"が含まれていない場合、自動的に`filename`文字列に追加されます。
  * `fractional_coords::Bool=true`: `true`の場合、原子の座標を分数座標として書き込みます。`false`の場合、直交座標を書き込みます。
  * `number_atoms::Bool=true`: 各原子に一意の識別子を与えるために、原子を"C1", "C2", "C3", ..., "N1", "N2", ...などとして書き込みます。
