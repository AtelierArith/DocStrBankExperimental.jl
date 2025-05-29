```
next_file(archive) => Union{IO, Nothing}
```

アーカイブ内の次のファイルを読み取り可能な `IO` オブジェクトまたは `nothing` を返します。

これは `first(iterate(archive))` を呼び出すのと同じです。
