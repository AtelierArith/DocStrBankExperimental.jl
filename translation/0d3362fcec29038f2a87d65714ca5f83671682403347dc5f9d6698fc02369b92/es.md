```
pwd() -> String
```

Obtiene el directorio de trabajo actual.

Véase también: [`cd`](@ref), [`tempdir`](@ref).

# Ejemplos

```julia-repl
julia> pwd()
"/home/JuliaUser"

julia> cd("/home/JuliaUser/Projects/julia")

julia> pwd()
"/home/JuliaUser/Projects/julia"
```
