```
zip_writefile(w::ZipWriter, name::AbstractString, data::AbstractVector{UInt8})
```

データを `name` という名前のファイルエントリとして書き込みます。

`zip_newfile` とは異なり、基盤となる IO は `Base.unsafe_write` と `Base.isopen` を実装する必要があります。`w` はその後書き込み不可になります。書き込まれたデータは圧縮されません。

参照: [`zip_newfile`](@ref)

# オプショナルキーワード

  * `comment::String=""`: エントリコメント、`ncodeunits(comment) ≤ typemax(UInt16)`。
  * `executable::Union{Nothing,Bool}=nothing`: ファイルを実行可能としてマークするには true に設定します。デフォルトは false です。
  * `external_attr::Union{Nothing,UInt32}=nothing`: 外部ファイル属性を手動で設定します: https://unix.stackexchange.com/questions/14705/the-zip-formats-external-file-attribute を参照してください。
