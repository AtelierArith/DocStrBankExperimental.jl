```
pwd() -> String
```

Geçerli çalışma dizinini alır.

Ayrıca bakınız: [`cd`](@ref), [`tempdir`](@ref).

# Örnekler

```julia-repl
julia> pwd()
"/home/JuliaUser"

julia> cd("/home/JuliaUser/Projects/julia")

julia> pwd()
"/home/JuliaUser/Projects/julia"
```
