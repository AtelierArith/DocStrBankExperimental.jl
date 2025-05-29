```
xsd_to_struct_module(xsd_path::AbstractString, output_dir::AbstractString)::String
```

Generate Julia module corresponding to the given xsd file. The resulting Julia module will be placed in the given `output_dir`. The module generated will have the same name as the xsd namespace defined in the given xsd file. The path to the file with the generated code is given as a return value. The file generated will have the approximately the same name as the given xsd file but with a ".jl" extension instead of ".xsd". To use the generated module include the generated file that is returned by this function, and then use or import the module.

# Examples

```julia-repl
julia> using XsdToStruct
julia> xsd_to_struct_module(joinpath("path", "to", "file.xsd"), joinpath("output", "dir"))
julia> include(joinpath("output", "dir", "file", "file.jl"))
julia> using file_xsd_namespace
```

or

```julia-repl
julia> using XsdToStruct
julia> xsd_to_struct_module(joinpath("path", "to", "file.xsd"), joinpath("output", "dir"))
julia> include(joinpath("output", "dir", "file", "file.jl"))
julia> import file_xsd_namespace
```
