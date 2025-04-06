```
walkdir(dir; topdown=true, follow_symlinks=false, onerror=throw)
```

Renvoie un itérateur qui parcourt l'arborescence des répertoires d'un répertoire. L'itérateur renvoie un tuple contenant `(rootpath, dirs, files)`. L'arborescence des répertoires peut être parcourue de haut en bas ou de bas en haut. Si `walkdir` ou `stat` rencontre une `IOError`, il relancera l'erreur par défaut. Une fonction de gestion des erreurs personnalisée peut être fournie via l'argument clé `onerror`. `onerror` est appelé avec une `IOError` comme argument.

Voir aussi : [`readdir`](@ref).

# Exemples

```julia
for (root, dirs, files) in walkdir(".")
    println("Répertoires dans $root")
    for dir in dirs
        println(joinpath(root, dir)) # chemin vers les répertoires
    end
    println("Fichiers dans $root")
    for file in files
        println(joinpath(root, file)) # chemin vers les fichiers
    end
end
```

```julia-repl
julia> mkpath("my/test/dir");

julia> itr = walkdir("my");

julia> (root, dirs, files) = first(itr)
("my", ["test"], String[])

julia> (root, dirs, files) = first(itr)
("my/test", ["dir"], String[])

julia> (root, dirs, files) = first(itr)
("my/test/dir", String[], String[])
```
