```
cd(dir::AbstractString=homedir())
```

Setzen Sie das aktuelle Arbeitsverzeichnis.

Siehe auch: [`pwd`](@ref), [`mkdir`](@ref), [`mkpath`](@ref), [`mktempdir`](@ref).

# Beispiele

```julia-repl
julia> cd("/home/JuliaUser/Projects/julia")

julia> pwd()
"/home/JuliaUser/Projects/julia"

julia> cd()

julia> pwd()
"/home/JuliaUser"
```
