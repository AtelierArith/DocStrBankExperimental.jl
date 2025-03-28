```
splitdir(path::AbstractString) -> (AbstractString, AbstractString)
```

Divise un chemin en un tuple contenant le nom du répertoire et le nom du fichier.

# Exemples

```jldoctest
julia> splitdir("/home/myuser")
("/home", "myuser")
```
