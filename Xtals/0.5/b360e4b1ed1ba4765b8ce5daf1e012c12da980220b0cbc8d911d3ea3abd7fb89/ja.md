```
write_mol2(xtal, filename="my_xtal.mol2")
```

`Crystal`をmol2形式でディスクに書き込みます。原子、結合、および単位セルが含まれます。

# 引数

  * `xtal::Crystal` : エクスポートする結晶
  * `filename::AbstractString` : (オプション) 保存するファイルの名前。デフォルトでは、ファイルは`xtal.name`から自動的に名前が付けられます。
