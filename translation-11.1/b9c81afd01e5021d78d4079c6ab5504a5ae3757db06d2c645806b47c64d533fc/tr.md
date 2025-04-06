```
cd(f::Function, dir::AbstractString=homedir())
```

Geçici olarak mevcut çalışma dizinini `dir` olarak değiştirir, `f` fonksiyonunu uygular ve sonunda orijinal dizine geri döner.

# Örnekler

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
