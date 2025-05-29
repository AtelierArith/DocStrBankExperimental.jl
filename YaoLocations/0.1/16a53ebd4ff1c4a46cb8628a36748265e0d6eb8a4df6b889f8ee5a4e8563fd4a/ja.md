```
Locations <: AbstractLocations
```

量子回路内の位置を注釈するための型。

```
Locations(x)
```

生の位置ステートメントから`Locations`オブジェクトを作成します。有効なストレージタイプは次のとおりです。

  * `Int`: 単一の位置
  * `NTuple{N, Int}`: 位置のリスト
  * `UnitRange{Int}`: 連続した位置

他のタイプは`Tuple`を介してストレージタイプに変換されます。
