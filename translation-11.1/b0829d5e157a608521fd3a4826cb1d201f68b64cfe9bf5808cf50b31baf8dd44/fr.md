```
closewrite(stream)
```

Arrête la moitié écriture d'un flux I/O duplex complet. Effectue d'abord un [`flush`](@ref). Informe l'autre extrémité qu'aucune donnée supplémentaire ne sera écrite dans le fichier sous-jacent. Cela n'est pas pris en charge par tous les types d'E/S.

Si implémenté, `closewrite` provoque que les appels ultérieurs à `read` ou `eof` qui bloqueraient lancent plutôt EOF ou retournent vrai, respectivement. Si le flux est déjà fermé, cela est idempotent.

# Exemples

```jldoctest
julia> io = Base.BufferStream(); # cela ne bloque jamais, donc nous pouvons lire et écrire sur la même tâche

julia> write(io, "request");

julia> # appeler `read(io)` ici bloquerait indéfiniment

julia> closewrite(io);

julia> read(io, String)
"request"
```
