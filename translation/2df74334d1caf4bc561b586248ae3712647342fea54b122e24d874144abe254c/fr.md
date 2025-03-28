```
cglobal((symbol, library) [, type=Cvoid])
```

Obtenez un pointeur vers une variable globale dans une bibliothèque partagée exportée en C, spécifiée exactement comme dans [`ccall`](@ref). Renvoie un `Ptr{Type}`, par défaut `Ptr{Cvoid}` si aucun argument `Type` n'est fourni. Les valeurs peuvent être lues ou écrites par [`unsafe_load`](@ref) ou [`unsafe_store!`](@ref), respectivement.
