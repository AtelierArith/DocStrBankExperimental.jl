```
skipchars(predicate, io::IO; linecomment=nothing)
```

Avancez le flux `io` de sorte que le prochain caractère lu soit le premier restant pour lequel `predicate` renvoie `false`. Si l'argument clé `linecomment` est spécifié, tous les caractères de ce caractère jusqu'au début de la ligne suivante sont ignorés.

# Exemples

```jldoctest
julia> buf = IOBuffer("    text")
IOBuffer(data=UInt8[...], readable=true, writable=false, seekable=true, append=false, size=8, maxsize=Inf, ptr=1, mark=-1)

julia> skipchars(isspace, buf)
IOBuffer(data=UInt8[...], readable=true, writable=false, seekable=true, append=false, size=8, maxsize=Inf, ptr=5, mark=-1)

julia> String(readavailable(buf))
"text"
```
