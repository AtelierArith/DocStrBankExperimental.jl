```
mkpath(path::AbstractString; mode::Unsigned = 0o777)
```

Créez tous les répertoires intermédiaires dans le `path` selon les besoins. Les répertoires sont créés avec les permissions `mode` qui par défaut est `0o777` et est modifié par le masque de création de fichiers actuel. Contrairement à [`mkdir`](@ref), `mkpath` ne renvoie pas d'erreur si `path` (ou des parties de celui-ci) existe déjà. Cependant, une erreur sera lancée si `path` (ou des parties de celui-ci) pointe vers un fichier existant. Retourne `path`.

Si `path` inclut un nom de fichier, vous voudrez probablement utiliser `mkpath(dirname(path))` pour éviter de créer un répertoire en utilisant le nom de fichier.

# Exemples

```julia-repl
julia> cd(mktempdir())

julia> mkpath("my/test/dir") # crée trois répertoires
"my/test/dir"

julia> readdir()
1-élément Array{String,1}:
 "my"

julia> cd("my")

julia> readdir()
1-élément Array{String,1}:
 "test"

julia> readdir("test")
1-élément Array{String,1}:
 "dir"

julia> mkpath("intermediate_dir/actually_a_directory.txt") # crée deux répertoires
"intermediate_dir/actually_a_directory.txt"

julia> isdir("intermediate_dir/actually_a_directory.txt")
true

```
