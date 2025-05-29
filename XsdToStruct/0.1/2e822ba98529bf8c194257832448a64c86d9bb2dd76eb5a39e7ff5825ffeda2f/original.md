```
generate_modules(xsd_locations::Dict{AbstractString, AbstractString}, xsd_modules_path::AbstractString)::Nothing
```

Generate modules from the given locations. The `xsd_locations` should be a dict which maps xsd names to their locations. The location can either be a path to a file, or a directory where the xsd file is located, or a URL where the xsd file can downloaded from. The generated modules are placed into the given `xsd_modules_path`. It is recomended for any packages that use generated modules to use this function in a build script to generate up to date modules on the fly.

# Examples

Let's assume we have a folder "xsd*files" which contains the xsd files: "file*1.xsd", "file*2.xsd", and "file*3.xsd", and we also have a file located at a URL. We can then generate modules for them and place these modules into the folder "xsd_modules" as follows:

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
