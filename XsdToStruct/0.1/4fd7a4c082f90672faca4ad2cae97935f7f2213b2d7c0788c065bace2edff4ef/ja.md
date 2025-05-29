```
xsd_to_struct_module(xsd_path::AbstractString, output_dir::AbstractString)::String
```

与えられた xsd ファイルに対応する Julia モジュールを生成します。生成された Julia モジュールは、指定された `output_dir` に配置されます。生成されるモジュールは、与えられた xsd ファイルで定義された xsd 名前空間と同じ名前になります。生成されたコードのファイルへのパスは、戻り値として与えられます。生成されたファイルは、与えられた xsd ファイルとほぼ同じ名前になりますが、拡張子が ".xsd" の代わりに ".jl" になります。生成されたモジュールを使用するには、この関数によって返された生成されたファイルをインクルードし、その後モジュールを使用またはインポートします。

# 例

```julia-repl
julia> using XsdToStruct
julia> xsd_to_struct_module(joinpath("path", "to", "file.xsd"), joinpath("output", "dir"))
julia> include(joinpath("output", "dir", "file", "file.jl"))
julia> using file_xsd_namespace
```

または

```julia-repl
julia> using XsdToStruct
julia> xsd_to_struct_module(joinpath("path", "to", "file.xsd"), joinpath("output", "dir"))
julia> include(joinpath("output", "dir", "file", "file.jl"))
julia> import file_xsd_namespace
```
