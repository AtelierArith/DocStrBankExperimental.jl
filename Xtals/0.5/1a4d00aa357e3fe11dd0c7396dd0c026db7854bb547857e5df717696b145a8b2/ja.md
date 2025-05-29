```
write_cssr(xtal, "myxtal.cssr")
write_cssr(xtal) # uses xtal.name to guess desired filename.
```

結晶構造を `.cssr` 形式で書き出します。

# 引数

  * `xtal::Crystal`: ファイルに書き出す結晶
  * `filename::AbstractString`: 書き出すファイル名。デフォルトは `pwd()` に `.cssr` ファイルを書き出します。`filename` に `.cssr` が含まれていない場合は、追加されます。
  * `quiet::Bool` : （オプション）コンソール出力を抑制するには `true` に設定します。
