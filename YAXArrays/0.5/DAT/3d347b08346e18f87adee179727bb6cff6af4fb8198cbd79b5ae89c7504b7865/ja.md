```
fittable(tab,o,fitsym;by=(),weight=nothing)
```

イテラブルなテーブル `tab` をループし、指定された値を通じて OnlineStat `o` をフィッティングします。オプションで、グループ化するフィールド（またはタプル）を指定できます。グループ化指定子は、グループ化するエントリを示すシンボルまたはテーブル行からグループを計算する匿名関数のいずれかです。

例えば、以下は国と月でグループ化され、グリッドセル面積で重み付けされたキューブの加重平均を計算します：

```julia
fittable(iter,WeightedMean,:tair,weight=(i->abs(cosd(i.lat))),by=(i->month(i.time),:country))
```
