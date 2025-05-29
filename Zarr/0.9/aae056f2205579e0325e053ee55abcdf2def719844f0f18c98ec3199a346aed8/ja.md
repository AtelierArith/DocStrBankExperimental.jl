```
zopen(s::AbstractStore, mode="r"; consolidated = false, path = "", lru = 0)
```

Store `s` で zarr 配列またはグループを開きます。`consolidated` が "true" に設定されている場合、Zarr は python zarr の `consolidate_metadata` 関数によって作成された統合メタデータフィールドを検索します。これにより、大きな zarr グループのメタデータ解析が大幅に高速化される可能性があります。`lru` を 0 より大きい値に設定すると、以前にアクセスされたチャンクがキャッシュされ、連続した読み取りがキャッシュから行われます。ここで、`lru` はメモリに残るチャンクの数を示します。
