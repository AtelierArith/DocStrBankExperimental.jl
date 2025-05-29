```
zip_newfile(w::ZipWriter, name::AbstractString; 
    compress::Bool=false,
)
```

`name`という名前の新しいファイルエントリを開始します。

これにより、現在開いているエントリがコミットされ、`w`がファイルエントリ`name`に対して書き込み可能になります。

`w`の基盤となる`IO`は、この関数を使用するためにシーク可能でなければなりません。そうでない場合は[`zip_writefile`](@ref)を参照してください。

# オプションのキーワード

  * `comment::String=""`: エントリコメント、`ncodeunits(comment) ≤ typemax(UInt16)`。
  * `compress::Bool=false`: falseの場合、圧縮は使用されず、他の圧縮オプションは無視されます。
  * `compression_level::Int=-1`: 1が最速、9が最小のファイルサイズです。0は圧縮なし、-1は速度とファイルサイズの良い妥協点です。
  * `compression_method=Deflate`: 現在、`Deflate`と`Store`のみがサポートされています。
  * `executable::Union{Nothing,Bool}=nothing`: ファイルを実行可能としてマークするにはtrueに設定します。デフォルトはfalseです。
  * `external_attrs::Union{Nothing,UInt32}=nothing`: 外部ファイル属性を手動でオーバーライドします。詳細はhttps://unix.stackexchange.com/questions/14705/the-zip-formats-external-file-attributeを参照してください。
