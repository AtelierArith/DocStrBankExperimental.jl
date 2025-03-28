```
isopen(object) -> Bool
```

Déterminez si un objet - tel qu'un flux ou un minuteur - n'est pas encore fermé. Une fois qu'un objet est fermé, il ne produira jamais un nouvel événement. Cependant, comme un flux fermé peut encore avoir des données à lire dans son tampon, utilisez [`eof`](@ref) pour vérifier la possibilité de lire des données. Utilisez le package `FileWatching` pour être informé lorsque un flux pourrait être écrivable ou lisible.

# Exemples

```jldoctest
julia> io = open("my_file.txt", "w+");

julia> isopen(io)
true

julia> close(io)

julia> isopen(io)
false
```
