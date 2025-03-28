```
Mmap.Anonymous(name::AbstractString="", readonly::Bool=false, create::Bool=true)
```

Crée un objet de type `IO` pour créer une mémoire mappée à zéro qui n'est pas liée à un fichier pour une utilisation dans [`mmap`](@ref mmap). Utilisé par `SharedArray` pour créer des tableaux de mémoire partagée.

# Exemples

```jldoctest
julia> using Mmap

julia> anon = Mmap.Anonymous();

julia> isreadable(anon)
true

julia> iswritable(anon)
true

julia> isopen(anon)
true
```
