```
xsd_to_struct_module(xsd_path::AbstractString)::String
```

与えられた xsd ファイルに対応する Julia モジュールを生成します。生成された Julia モジュールは、与えられた xsd ファイルと同じディレクトリに配置されます。生成されたコードのファイルへのパスは、戻り値として与えられます。

# 例

```julia-repl
julia> using XsdToStruct
julia> xsd_to_struct_module(joinpath("path", "to", "file.xsd"))
julia> include(joinpath("path", "to", "file", "file.jl"))
julia> using file_xsd_namespace
```

または

```julia-repl
julia> using XsdToStruct
julia> xsd_to_struct_module(joinpath("path", "to", "file.xsd"))
julia> include(joinpath("path", "to", "file", "file.jl"))
julia> import file_xsd_namespace
```
