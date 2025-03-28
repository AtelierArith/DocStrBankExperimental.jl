```
digest!(context)
```

Finalisez le contexte SHA et renvoyez le hachage sous forme de tableau d'octets (Array{Uint8, 1}). Mettre à jour le contexte après avoir appelé `digest!` sur celui-ci entraînera une erreur.

# Exemples

```julia-repl
julia> ctx = SHA1_CTX()
État de hachage SHA1

julia> update!(ctx, b"data to to be hashed")

julia> digest!(ctx)
Tableau de 20 éléments Array{UInt8,1}:
 0x83
 0xe4
 ⋮
 0x89
 0xf5

julia> update!(ctx, b"more data")
ERREUR: Impossible de mettre à jour CTX après que `digest!` a été appelé sur celui-ci
[...]
```
