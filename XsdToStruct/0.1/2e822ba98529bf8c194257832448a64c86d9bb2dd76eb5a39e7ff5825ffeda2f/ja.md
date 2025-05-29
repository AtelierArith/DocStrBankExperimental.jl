```
generate_modules(xsd_locations::Dict{AbstractString, AbstractString}, xsd_modules_path::AbstractString)::Nothing
```

指定された場所からモジュールを生成します。`xsd_locations`は、xsd名をその場所にマッピングする辞書である必要があります。場所は、ファイルへのパス、xsdファイルがあるディレクトリ、またはxsdファイルをダウンロードできるURLのいずれかです。生成されたモジュールは、指定された`xsd_modules_path`に配置されます。生成されたモジュールを使用するパッケージは、ビルドスクリプト内でこの関数を使用して、最新のモジュールを動的に生成することをお勧めします。

# 例

"xsd*files"というフォルダーに"xsdファイル"が含まれていると仮定しましょう："file*1.xsd"、"file*2.xsd"、および"file*3.xsd"、さらにURLに位置するファイルもあります。それらのモジュールを生成し、これらのモジュールを"xsd_modules"フォルダーに配置することができます。

```julia-repl
julia> using XsdToStruct
julia> xsd_locations = Dict(
    "local_file_1" => joinpath("path", "to", "xsd_files", "file_1.xsd"),
    "local_file_2" => joinpath("path", "to", "xsd_files"),
    "local_file_3" => joinpath("path", "to", "xsd_files"),
    "remote_file" => "https://url.to.last/xsd/file"
)
julia> xsd_modules_path = joinpath("output", "path", "for", "xsd", "modules")
julia> generate_modules(xsd_locations, xsd_modules_path)
```
