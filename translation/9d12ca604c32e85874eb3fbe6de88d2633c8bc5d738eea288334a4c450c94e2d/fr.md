```
PersistentDict
```

`PersistentDict` est un dictionnaire implémenté comme un trie mappé par tableau de hachage, qui est optimal pour les situations où vous avez besoin de persistance, chaque opération renvoie un nouveau dictionnaire distinct du précédent, mais l'implémentation sous-jacente est efficace en termes d'espace et peut partager le stockage entre plusieurs dictionnaires distincts.

!!! note
    Il se comporte comme un IdDict.


```julia
PersistentDict(KV::Pair)
```

# Exemples

```jldoctest
julia> dict = Base.PersistentDict(:a=>1)
Base.PersistentDict{Symbol, Int64} avec 1 entrée :
  :a => 1

julia> dict2 = Base.delete(dict, :a)
Base.PersistentDict{Symbol, Int64}()

julia> dict3 = Base.PersistentDict(dict, :a=>2)
Base.PersistentDict{Symbol, Int64} avec 1 entrée :
  :a => 2
```
