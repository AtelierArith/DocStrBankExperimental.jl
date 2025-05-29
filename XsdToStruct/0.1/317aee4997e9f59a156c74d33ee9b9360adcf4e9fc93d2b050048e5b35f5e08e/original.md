```
xsd_to_struct_module(xsd_path::AbstractString)::String
```

Generate Julia module corresponding to the given xsd file. The resulting Julia module will be placed in the same directory as the given xsd file. The path to the file with the generated code is given as a return value.

# Examples

```julia-repl
julia> using XsdToStruct
julia> xsd_to_struct_module(joinpath("path", "to", "file.xsd"))
julia> include(joinpath("path", "to", "file", "file.jl"))
julia> using file_xsd_namespace
```

or

```julia-repl
julia> using XsdToStruct
julia> xsd_to_struct_module(joinpath("path", "to", "file.xsd"))
julia> include(joinpath("path", "to", "file", "file.jl"))
julia> import file_xsd_namespace
```
