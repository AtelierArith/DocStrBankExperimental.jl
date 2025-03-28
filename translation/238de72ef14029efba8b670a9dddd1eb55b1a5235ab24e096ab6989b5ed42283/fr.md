```
mkdir(path::AbstractString; mode::Unsigned = 0o777)
```

Créez un nouveau répertoire avec le nom `path` et les permissions `mode`. `mode` par défaut est `0o777`, modifié par le masque de création de fichiers actuel. Cette fonction ne crée jamais plus d'un répertoire. Si le répertoire existe déjà, ou si certains répertoires intermédiaires n'existent pas, cette fonction lance une erreur. Voir [`mkpath`](@ref) pour une fonction qui crée tous les répertoires intermédiaires requis. Retourne `path`.

# Exemples

```julia-repl
julia> mkdir("testingdir")
"testingdir"

julia> cd("testingdir")

julia> pwd()
"/home/JuliaUser/testingdir"
```
