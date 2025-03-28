```
PersistentDict
```

`PersistentDict` es un diccionario implementado como un trie mapeado de matriz hash, que es óptimo para situaciones donde necesitas persistencia, cada operación devuelve un nuevo diccionario separado del anterior, pero la implementación subyacente es eficiente en espacio y puede compartir almacenamiento entre múltiples diccionarios separados.

!!! nota
    Se comporta como un IdDict.


```julia
PersistentDict(KV::Pair)
```

# Ejemplos

```jldoctest
julia> dict = Base.PersistentDict(:a=>1)
Base.PersistentDict{Symbol, Int64} con 1 entrada:
  :a => 1

julia> dict2 = Base.delete(dict, :a)
Base.PersistentDict{Symbol, Int64}()

julia> dict3 = Base.PersistentDict(dict, :a=>2)
Base.PersistentDict{Symbol, Int64} con 1 entrada:
  :a => 2
```
