```
Base64EncodePipe(ostream)
```

Renvoie un nouveau flux d'E/S en écriture seule, qui convertit tous les octets écrits dans celui-ci en octets ASCII encodés en base64 écrits dans `ostream`. Appeler [`close`](@ref) sur le flux `Base64EncodePipe` est nécessaire pour compléter l'encodage (mais ne ferme pas `ostream`).

# Exemples

```jldoctest
julia> io = IOBuffer();

julia> iob64_encode = Base64EncodePipe(io);

julia> write(iob64_encode, "Hello!")
6

julia> close(iob64_encode);

julia> str = String(take!(io))
"SGVsbG8h"

julia> String(base64decode(str))
"Hello!"
```
