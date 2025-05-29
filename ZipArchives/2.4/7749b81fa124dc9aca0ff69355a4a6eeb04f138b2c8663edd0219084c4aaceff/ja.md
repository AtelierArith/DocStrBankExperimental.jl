```
struct ZipReader{T<:AbstractVector{UInt8}}
ZipReader(buffer::AbstractVector{UInt8})
```

`buffer`内のバイトをZIPアーカイブとして表示します。

配列は読み取り中に変更されてはいけません。

`zip_nentries(r::ZipReader)::Int`はアーカイブ内のエントリの数を返します。

`zip_names(r::ZipReader)::Vector{String}`はアーカイブ内のすべてのエントリの名前を返します。

次の関数はアーカイブ内のエントリに関する情報を取得します：

エントリは`1:zip_nentries(r)`からインデックス付けされます。

1. `zip_name(r::ZipReader, i::Integer)::String`
2. `zip_uncompressed_size(r::ZipReader, i::Integer)::UInt64`

`zip_test_entry(r::ZipReader, i::Integer)::Nothing`はエントリが有効であり、良好なチェックサムを持っているかを確認します。

`zip_openentry`と`zip_readentry`はエントリからデータを読み取るために使用できます。

`parent`関数は基になるバッファを取得するために使用できます。

# マルチスレッド

返された`ZipReader`オブジェクトは複数のスレッドから安全に使用できます。ただし、`zip_openentry`によって返されるストリームには、一度に1つのスレッドのみがアクセスする必要があります。
