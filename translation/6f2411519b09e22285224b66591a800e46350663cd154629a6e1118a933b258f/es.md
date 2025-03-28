```
mkpath(path::AbstractString; mode::Unsigned = 0o777)
```

Crea todos los directorios intermedios en el `path` según sea necesario. Los directorios se crean con los permisos `mode`, que por defecto es `0o777` y se modifica por la máscara de creación de archivos actual. A diferencia de [`mkdir`](@ref), `mkpath` no genera un error si `path` (o partes de él) ya existe. Sin embargo, se lanzará un error si `path` (o partes de él) apunta a un archivo existente. Devuelve `path`.

Si `path` incluye un nombre de archivo, probablemente querrás usar `mkpath(dirname(path))` para evitar crear un directorio usando el nombre del archivo.

# Ejemplos

```julia-repl
julia> cd(mktempdir())

julia> mkpath("my/test/dir") # crea tres directorios
"my/test/dir"

julia> readdir()
1-element Array{String,1}:
 "my"

julia> cd("my")

julia> readdir()
1-element Array{String,1}:
 "test"

julia> readdir("test")
1-element Array{String,1}:
 "dir"

julia> mkpath("intermediate_dir/actually_a_directory.txt") # crea dos directorios
"intermediate_dir/actually_a_directory.txt"

julia> isdir("intermediate_dir/actually_a_directory.txt")
true

```
