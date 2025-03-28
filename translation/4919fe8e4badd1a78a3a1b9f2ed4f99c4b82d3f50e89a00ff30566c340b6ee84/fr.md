```
stringmime(mime, x; context=nothing)
```

Renvoie un `AbstractString` contenant la représentation de `x` dans le type `mime` demandé. Cela est similaire à [`repr(mime, x)`](@ref) sauf que les données binaires sont encodées en base64 sous forme de chaîne ASCII.

L'argument clé optionnel `context` peut être défini sur une paire `:key=>value` ou un objet `IO` ou [`IOContext`](@ref) dont les attributs sont utilisés pour le flux d'E/S passé à [`show`](@ref).
