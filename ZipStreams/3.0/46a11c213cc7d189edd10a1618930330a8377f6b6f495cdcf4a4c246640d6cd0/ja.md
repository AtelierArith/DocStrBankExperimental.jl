```
unzip_files(archive; output_path::AbstractString=".", make_path::Bool=false)
unzip_files(archive, files; [keyword_args])
```

`archive`から`files`を解凍します。`files`が指定されていない場合は、すべてのファイルを抽出します。

このメソッドはアーカイブを開き、アーカイブされたファイルを反復処理し、それらを`output_path`をルートとするディレクトリツリーにディスクに書き込みます。`make_path`が`true`で、`output_path`が存在しない場合は、作成されます。

ファイルがアーカイブからどのように読み取られるかについての詳細は、[`zipsource`](@ref)および[`next_file`](@ref)を参照してください。
