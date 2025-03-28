```
PersistentDict
```

`PersistentDict` ist ein Wörterbuch, das als Hash-Array-mapped Trie implementiert ist, was optimal für Situationen ist, in denen Sie Persistenz benötigen. Jede Operation gibt ein neues Wörterbuch zurück, das von dem vorherigen getrennt ist, aber die zugrunde liegende Implementierung ist speichereffizient und kann Speicherplatz über mehrere separate Wörterbücher hinweg teilen.

!!! Hinweis     Es verhält sich wie ein IdDict.

```julia
PersistentDict(KV::Pair)
```

# Beispiele

```jldoctest
julia> dict = Base.PersistentDict(:a=>1)
Base.PersistentDict{Symbol, Int64} mit 1 Eintrag:
  :a => 1

julia> dict2 = Base.delete(dict, :a)
Base.PersistentDict{Symbol, Int64}()

julia> dict3 = Base.PersistentDict(dict, :a=>2)
Base.PersistentDict{Symbol, Int64} mit 1 Eintrag:
  :a => 2
```
