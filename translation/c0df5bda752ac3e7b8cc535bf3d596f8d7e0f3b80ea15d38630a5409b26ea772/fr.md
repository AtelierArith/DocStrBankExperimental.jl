```
rm(path::AbstractString; force::Bool=false, recursive::Bool=false)
```

Supprime le fichier, le lien ou le répertoire vide à l'emplacement donné. Si `force=true` est passé, un chemin non existant n'est pas considéré comme une erreur. Si `recursive=true` est passé et que le chemin est un répertoire, alors tout le contenu est supprimé de manière récursive.

# Exemples

```jldoctest
julia> mkpath("my/test/dir");

julia> rm("my", recursive=true)

julia> rm("this_file_does_not_exist", force=true)

julia> rm("this_file_does_not_exist")
ERROR: IOError: unlink("this_file_does_not_exist"): no such file or directory (ENOENT)
Stacktrace:
[...]
```
