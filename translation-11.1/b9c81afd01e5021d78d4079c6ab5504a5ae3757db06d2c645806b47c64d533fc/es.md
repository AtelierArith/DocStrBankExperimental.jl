```
cd(f::Function, dir::AbstractString=homedir())
```

Cambia temporalmente el directorio de trabajo actual a `dir`, aplica la función `f` y finalmente regresa al directorio original.

# Ejemplos

```julia-repl
julia> pwd()
"/home/JuliaUser"

julia> cd(readdir, "/home/JuliaUser/Projects/julia")
34-element Array{String,1}:
 ".circleci"
 ".freebsdci.sh"
 ".git"
 ".gitattributes"
 ".github"
 ⋮
 "test"
 "ui"
 "usr"
 "usr-staging"

julia> pwd()
"/home/JuliaUser"
```
