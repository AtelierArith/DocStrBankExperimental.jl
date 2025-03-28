```
cd(f::Function, dir::AbstractString=homedir())
```

Ändert vorübergehend das aktuelle Arbeitsverzeichnis in `dir`, wendet die Funktion `f` an und kehrt schließlich zum ursprünglichen Verzeichnis zurück.

# Beispiele

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
