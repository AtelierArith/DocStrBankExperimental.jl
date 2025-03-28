```
splitext(path::AbstractString) -> (String, String)
```

Si le dernier composant d'un chemin contient un ou plusieurs points, divisez le chemin en tout ce qui se trouve avant le dernier point et tout ce qui inclut et après le point. Sinon, renvoyez un tuple de l'argument non modifié et de la chaîne vide. "splitext" est l'abréviation de "split extension".

# Exemples

```jldoctest
julia> splitext("/home/myuser/example.jl")
("/home/myuser/example", ".jl")

julia> splitext("/home/myuser/example.tar.gz")
("/home/myuser/example.tar", ".gz")

julia> splitext("/home/my.user/example")
("/home/my.user/example", "")
```
