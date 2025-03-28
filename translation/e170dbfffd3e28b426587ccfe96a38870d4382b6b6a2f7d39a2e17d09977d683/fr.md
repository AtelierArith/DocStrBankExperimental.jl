```
IOContext
```

`IOContext` fournit un mécanisme pour passer des paramètres de configuration de sortie entre les méthodes [`show`](@ref).

En résumé, c'est un dictionnaire immuable qui est une sous-classe de `IO`. Il prend en charge les opérations de dictionnaire standard telles que [`getindex`](@ref), et peut également être utilisé comme un flux d'E/S.
