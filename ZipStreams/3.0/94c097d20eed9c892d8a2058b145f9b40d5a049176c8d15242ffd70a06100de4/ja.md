```
zip_files(out_filename, files; [keyword_args])
zip_files(out_filename, dir; recurse_directories=false, [keyword_args])
```

ディスク上のファイルからアーカイブを作成します。

アーカイブ `out_filename` は、以下に示すキーワード引数を分割して `zipsink` メソッドを使用して作成されます。 `in_filename` は単一のパスまたはディスク上の複数のパスのベクターであることができます。ファイルは、現在のディレクトリ（`"."`）とファイルのフルパスとの間の最も近い共通相対パスに一致するパスでアーカイブに書き込まれます。したがって、`archive_filename` が "/a/b/archive.zip" で、`files` の1つが "/a/c/file" の場合、ファイルは "c/file" というパスで書き込まれます。

`dir` がディレクトリであり、`recurse_directories` が `true` の場合、ディレクトリを横断する際に見つかったすべてのファイルとディレクトリがアーカイブに追加されます。`recurse_directories` が `false`（デフォルト）である場合、`dir` のサブディレクトリは横断されません。

すべてのファイルは、`open(zipsink, fn; keyword_args..)` で指定されたデフォルト引数を使用してアーカイブに書き込まれ、特別なキーワード引数は以下に示すように分割されます。

# 引数

  * `out_filename::AbstractString`: 作成する出力アーカイブファイル名。
  * `files::AbstractVector{<:AbstractString}`: 新しく作成されたアーカイブに追加するファイルパスのリスト。
  * `dir::AbstractString`: 新しく作成されたアーカイブに追加するディレクトリへのパス。

# キーワード引数

  * `utf8::Bool = true`: ファイル名とコメントにUTF-8エンコーディングを使用します（`false` の場合は IBM437 を使用）。
  * `archive_comment::AbstractString = ""`: 中央ディレクトリに追加するアーカイブコメント文字列で、`zipsink` に `comment` キーワードを渡すのと同等です。
  * `file_options::Dict{String, Any} = nothing`: アーカイブに追加されたファイル名が `file_options` のキーと *正確に* 一致する場合、そのキーに対応する値がそのファイルのためのキーワード引数としてスプラットされ、以下に示すように渡されたキーワード引数を上書きします。
  * その他のすべてのキーワード引数: `open(sink, filename)` メソッドに変更されずに渡されます。

各メソッドで利用可能なオプションのキーワード引数についての詳細は、[`open(::ZipArchiveSink, ::AbstractString)`](@ref) および [`zipsink`](@ref) を参照してください。
