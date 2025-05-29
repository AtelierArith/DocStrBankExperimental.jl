```
fittable(tab,o,fitsym;by=(),weight=nothing)
```

イテラブルなテーブル `tab` をループし、指定された `fitsym` の値を使って OnlineStat `o` をフィッティングします。オプションで、グループ化するためのフィールド（またはタプル）を指定できます。グループ化の指定子は、グループ化するエントリを示すシンボルか、テーブルの行からグループを計算する無名関数のいずれかです。

例えば、以下のコードは、国と月でグループ化し、グリッドセルの面積で重み付けされたキューブの加重平均を計算します：

```julia
fittable(iter,WeightedMean,:tair,weight=(i->abs(cosd(i.lat))),by=(i->month(i.time),:country))
```
