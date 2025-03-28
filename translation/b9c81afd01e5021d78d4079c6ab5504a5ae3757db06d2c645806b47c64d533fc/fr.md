```
cd(f::Function, dir::AbstractString=homedir())
```

Change temporairement le répertoire de travail actuel en `dir`, applique la fonction `f` et retourne finalement au répertoire d'origine.

# Exemples

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
