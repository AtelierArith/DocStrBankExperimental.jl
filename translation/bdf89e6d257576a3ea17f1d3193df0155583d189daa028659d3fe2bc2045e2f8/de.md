```
readdir(dir::AbstractString=pwd();
    join::Bool = false,
    sort::Bool = true,
) -> Vector{String}
```

Gibt die Namen im Verzeichnis `dir` oder im aktuellen Arbeitsverzeichnis zurück, wenn nichts angegeben ist. Wenn `join` falsch ist, gibt `readdir` nur die Namen im Verzeichnis so zurück, wie sie sind; wenn `join` wahr ist, gibt es `joinpath(dir, name)` für jeden `name` zurück, sodass die zurückgegebenen Strings vollständige Pfade sind. Wenn Sie absolute Pfade zurückbekommen möchten, rufen Sie `readdir` mit einem absoluten Verzeichnispfad und `join` auf true auf.

Standardmäßig sortiert `readdir` die Liste der Namen, die es zurückgibt. Wenn Sie das Sortieren der Namen überspringen und sie in der Reihenfolge erhalten möchten, in der das Dateisystem sie auflistet, können Sie `readdir(dir, sort=false)` verwenden, um auf das Sortieren zu verzichten.

Siehe auch: [`walkdir`](@ref).

!!! compat "Julia 1.4"
    Die Schlüsselwortargumente `join` und `sort` erfordern mindestens Julia 1.4.


# Beispiele

```julia-repl
julia> cd("/home/JuliaUser/dev/julia")

julia> readdir()
30-element Array{String,1}:
 ".appveyor.yml"
 ".git"
 ".gitattributes"
 ⋮
 "ui"
 "usr"
 "usr-staging"

julia> readdir(join=true)
30-element Array{String,1}:
 "/home/JuliaUser/dev/julia/.appveyor.yml"
 "/home/JuliaUser/dev/julia/.git"
 "/home/JuliaUser/dev/julia/.gitattributes"
 ⋮
 "/home/JuliaUser/dev/julia/ui"
 "/home/JuliaUser/dev/julia/usr"
 "/home/JuliaUser/dev/julia/usr-staging"

julia> readdir("base")
145-element Array{String,1}:
 ".gitignore"
 "Base.jl"
 "Enums.jl"
 ⋮
 "version_git.sh"
 "views.jl"
 "weakkeydict.jl"

julia> readdir("base", join=true)
145-element Array{String,1}:
 "base/.gitignore"
 "base/Base.jl"
 "base/Enums.jl"
 ⋮
 "base/version_git.sh"
 "base/views.jl"
 "base/weakkeydict.jl"

julia> readdir(abspath("base"), join=true)
145-element Array{String,1}:
 "/home/JuliaUser/dev/julia/base/.gitignore"
 "/home/JuliaUser/dev/julia/base/Base.jl"
 "/home/JuliaUser/dev/julia/base/Enums.jl"
 ⋮
 "/home/JuliaUser/dev/julia/base/version_git.sh"
 "/home/JuliaUser/dev/julia/base/views.jl"
 "/home/JuliaUser/dev/julia/base/weakkeydict.jl"
```
