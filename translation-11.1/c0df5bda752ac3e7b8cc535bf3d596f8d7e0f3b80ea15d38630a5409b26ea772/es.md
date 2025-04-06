```
rm(path::AbstractString; force::Bool=false, recursive::Bool=false)
```

Elimina el archivo, enlace o directorio vacío en la ruta dada. Si se pasa `force=true`, una ruta no existente no se trata como un error. Si se pasa `recursive=true` y la ruta es un directorio, entonces todo el contenido se elimina recursivamente.

# Ejemplos

```jldoctest
julia> mkpath("my/test/dir");

julia> rm("my", recursive=true)

julia> rm("this_file_does_not_exist", force=true)

julia> rm("this_file_does_not_exist")
ERROR: IOError: unlink("this_file_does_not_exist"): no such file or directory (ENOENT)
Stacktrace:
[...]
```
