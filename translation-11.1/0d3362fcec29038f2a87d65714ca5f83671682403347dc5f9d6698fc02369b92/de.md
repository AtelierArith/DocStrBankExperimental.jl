```
pwd() -> String
```

Holen Sie das aktuelle Arbeitsverzeichnis.

Siehe auch: [`cd`](@ref), [`tempdir`](@ref).

# Beispiele

```julia-repl
julia> pwd()
"/home/JuliaUser"

julia> cd("/home/JuliaUser/Projects/julia")

julia> pwd()
"/home/JuliaUser/Projects/julia"
```
