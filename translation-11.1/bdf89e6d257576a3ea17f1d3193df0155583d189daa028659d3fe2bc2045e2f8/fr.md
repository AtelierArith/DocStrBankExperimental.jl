```
readdir(dir::AbstractString=pwd();
    join::Bool = false,
    sort::Bool = true,
) -> Vector{String}
```

Renvoie les noms dans le répertoire `dir` ou le répertoire de travail actuel si aucun n'est donné. Lorsque `join` est faux, `readdir` renvoie simplement les noms dans le répertoire tels quels ; lorsque `join` est vrai, il renvoie `joinpath(dir, name)` pour chaque `name` afin que les chaînes renvoyées soient des chemins complets. Si vous souhaitez obtenir des chemins absolus, appelez `readdir` avec un chemin de répertoire absolu et `join` défini sur vrai.

Par défaut, `readdir` trie la liste des noms qu'il renvoie. Si vous souhaitez ignorer le tri des noms et les obtenir dans l'ordre dans lequel le système de fichiers les liste, vous pouvez utiliser `readdir(dir, sort=false)` pour ne pas trier.

Voir aussi : [`walkdir`](@ref).

!!! compat "Julia 1.4"
    Les arguments de mot-clé `join` et `sort` nécessitent au moins Julia 1.4.


# Exemples

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
