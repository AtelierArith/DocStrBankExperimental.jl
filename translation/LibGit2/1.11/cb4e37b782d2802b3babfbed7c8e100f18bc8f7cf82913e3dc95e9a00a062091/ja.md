```
read!(idx::GitIndex, force::Bool = false) -> GitIndex
```

ディスク上で行われた変更を読み込むことによって `idx` の内容を更新します。たとえば、`idx` は、作成以来リポジトリにファイルが追加された場合に更新されることがあります。`force` が `true` の場合、メモリ内の変更（最後の [`write!`](@ref) 以降、または書き込みが行われていない場合は作成以来の `idx` の変更）は破棄されます。`force` が `false` の場合、インデックスデータは、ディスク上のデータが最後に `idx` に読み込まれた時から変更されている場合にのみ、ディスクから更新されます。
