```
normpath(path::AbstractString) -> String
```

Normaliza una ruta, eliminando las entradas "." y ".." y cambiando "/" al separador de ruta canónico para el sistema.

# Ejemplos

```jldoctest
julia> normpath("/home/myuser/../example.jl")
"/home/example.jl"

julia> normpath("Documents/Julia") == joinpath("Documents", "Julia")
true
```
