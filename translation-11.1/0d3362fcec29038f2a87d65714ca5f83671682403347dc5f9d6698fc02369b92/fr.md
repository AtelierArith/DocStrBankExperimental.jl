```
pwd() -> String
```

Obtenez le répertoire de travail actuel.

Voir aussi : [`cd`](@ref), [`tempdir`](@ref).

# Exemples

```julia-repl
julia> pwd()
"/home/JuliaUser"

julia> cd("/home/JuliaUser/Projects/julia")

julia> pwd()
"/home/JuliaUser/Projects/julia"
```
