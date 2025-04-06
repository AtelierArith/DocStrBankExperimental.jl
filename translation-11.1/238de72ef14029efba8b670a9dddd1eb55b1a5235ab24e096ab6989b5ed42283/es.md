```
mkdir(path::AbstractString; mode::Unsigned = 0o777)
```

Crea un nuevo directorio con el nombre `path` y permisos `mode`. `mode` tiene como valor predeterminado `0o777`, modificado por la máscara de creación de archivos actual. Esta función nunca crea más de un directorio. Si el directorio ya existe, o si algunos directorios intermedios no existen, esta función lanza un error. Consulta [`mkpath`](@ref) para una función que crea todos los directorios intermedios requeridos. Devuelve `path`.

# Ejemplos

```julia-repl
julia> mkdir("testingdir")
"testingdir"

julia> cd("testingdir")

julia> pwd()
"/home/JuliaUser/testingdir"
```
